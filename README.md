# Amazon
Repricing software for your inventory on Amazon.

The Amazon repricing software helps increase your sales by monitoring and automatically updating your inventory prices according to the current market. This saves countless hours of manually re-pricing hundreds, if not thousands, of listings.

### Features
* Find the lowest price listing with equivalent or better condition and either match or beat the price by $0.01
* Calculate profit earned from the listed price after shipping, tax, and Amazon fees
* Set price floor to desired minimum profit
* Set price ceiling to prevent offer from being delisted (happens when price is too high)
* Filter listings based on condition and seller rating

### How to Use
Create a text file in the `Amazon` directory with all of your product ASIN/ISBN-10 numbers and their condition. The condition number is as follows (also see `books.txt` as a sample file):  
| **Condition:**               | **Number:** |
|--------------------------|---------|
| New                      | 9       |
| Used - Like New          | 8       |
| Used - Very Good         | 7       |
| Used - Good              | 6       |
| Used - Acceptable        | 5       |
| Collectible - Like New   | 4       |
| Collectible - Very Good  | 3       |
| Collectible - Good       | 2       |
| Collectible - Acceptable | 1       |

When the program finishes executing, there will be a file inside the `Amazon` directory titled `<FileName>_out.txt`. The text file will contain an inventory list of all your products that met your minimum desired profit and their new prices.

For each product, the console (System.out) will print the name, the new price, and the net profit. If there are product(s) that did not meet your minimum desired profit, the console will also print a list of such product names at the end.

Invalid product ASIN or ISBN-10 numbers will be printed to System.out. Problems with network connection will throw an exception to System.err and terminate the program.

### Prerequisites
* Java JDK 1.7 or higher  
For convenience, you should add the `/bin` directory to the `PATH` environment variable.
* [jsoup](http://jsoup.org/)  
jsoup is a Java library for extracting and manipulating HTML data.

### Getting started
Clone the repository and `cd` into the same directory.  
`$ git clone http://github.com/rchen8/Amazon.git`  
`$ cd Amazon`

**Using Eclipse**
Select *File --> New --> Java Project*. Uncheck "Use default location". Under "Location" browse the directory of the Amazon repository. Click "Finish".  
To add the external JAR in the `lib` folder, right-click `jsoup-1.8.2.jar` and select *Build Path --> Add to Build Path*.

**Using Command Line**
`cd` into the `src` directory.  
`$ cd src`

To compile with the external JAR execute the following command (replacing `<path>` with the full file path to the `Amazon` directory).  
`$ javac -g -d <path>\lib -cp jsoup-1.8.2.jar Amazon.java`

To run (replacing `<path>` with the full file path to the `Amazon` directory).  
`$ java -cp <path>\lib\jsoup-1.8.2.jar;. Amazon`

### About
Copyright (c) 2015 Richard Chen under the GNU Lesser General Public License v3.0.  
Email: richardchen39@gmail.com

Please feel free to contact me if you have any questions or suggestions for improvements. If you're interested in development, fork this repository and submit a pull request. Contributions are welcome with open arms.

### TODO
* Login to Amazon seller using the [Amazon Developer API](http://login.amazon.com/documentation/combining-user-accounts)
* Parse the inventory page on Amazon seller to sync price updates
* GUI and I/O interfaces
* Simple way to add condition filters
* Parse tax information from HTML (cssQuery doesn't work on Amazon for tax)
* Optimize time to parse listings by only selecting the lowest price per condition