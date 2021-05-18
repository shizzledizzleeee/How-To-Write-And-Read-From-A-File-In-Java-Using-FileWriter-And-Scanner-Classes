# How-To-Write-And-Read-From-A-File-In-Java-Using-FileWriter-And-Scanner-Classes
How To Write And Read From A File In Java Using FileWriter And Scanner Classes

Article - http://mauricemuteti.info/how-to-write-and-read-from-a-file-in-java-using-filewriter-and-scanner-classes/
Video tutorial - https://www.youtube.com/watch?v=TrFfS0W7C_s

/*
 * This Tutorial Shows How To Read And Write Data To A Text File.
 * This is achieved by using filewriter and scanner classes to write and read data from files respectively.
 * Just copy this code to your IDE and test it. I have used Netbeans IDE.
 * http://mauricemuteti.info/how-to-write-and-read-from-a-file-in-java-using-filewriter-and-scanner-classes/
 */
 
 
package readandwritetoatextfileusingjava;

import java.io.File;
import java.io.FileNotFoundException;
import java.io.FileWriter;
import java.io.IOException;
import java.util.Scanner;

/**
 *
 * @author Authentic
 */
public class ReadAndWriteToATextFileUsingJava {

    /**
     * @param args the command line arguments
     */
    public static void main(String[] args) {
        // TODO code application logic here

        //FileName.
        String fileName = "data.txt";
        //Text To Be Written In A Text File.
        String content = "This Data Will Be Written To A Text File";
        //Calling Static Method for Writing Data To A Text File.
        writeToATextFile(fileName, content);
        //Reading data from a text file.
        readFromATextFile(fileName);
    }

    /**
     * Method for Writing Data To A Text File.
     *
     * @param fileName
     * @param Content
     */
    public static void writeToATextFile(String fileName, String Content) {

        //Creating/Declaring File Writer Object.
        FileWriter fileWriter = null;

        try {
            //Inside Try Catch Block.
            System.out.println("Inside Try Catch Block");
            //Initializing File Writer Object.
            fileWriter = new FileWriter(new File(fileName));
            //Writing to a text file.
            fileWriter.write(Content);
            //Printing On The Console.
            System.out.println("Data Written successfully");

        } catch (IOException ex) {

            //Catching Exceptions
            System.out.println("Error : " + ex.getMessage());
        } finally {

            //Finally Execute this code
            if (fileWriter != null) {
                try {
                    //Closing File Writer.
                    System.out.println("Closing File Writer.");
                    //Releasing Resources By Closing Objects.
                    fileWriter.close();
                } catch (IOException ex) {
                    //Catching Exceptions
                    System.out.println("Error : " + ex.getMessage());

                }
            }
        }
    }

    /**
     * Method for Reading Data From A Text File
     *
     * @param fileName
     */
    public static void readFromATextFile(String fileName) {

        //Creating Scanner Object.
        Scanner scannerObject = null;
        try {

            scannerObject = new Scanner(new File(fileName));
            System.out.println("\nReading Data From A Text File");
            //While loop - Looping throught text file lines to get all data.
            while (scannerObject.hasNext()) {
                //Store data from a text file in a variable
                String result = scannerObject.nextLine();
                //Print data on the console.
                System.out.println(result);
            }
        } catch (FileNotFoundException ex) {
            //Catching Exceptions
            System.out.println("Error : " + ex.getMessage());
        } finally {
            if (scannerObject != null) {
                System.out.println("Closing Scanner.");
                //Releasing Resources By Closing Objects
                //Closing Scanner Object.
                scannerObject.close();
            }
        }

    }

}
