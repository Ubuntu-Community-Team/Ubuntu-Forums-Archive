---
title: "Cant read from std::cin while reading from serial port using libserial"
date: 2018-02-28
forum: Networking &amp; Wireless
---

### Post by shome on 2018-02-28
I am trying to read from the serial port using libserial. The code sets up the serial port communication with the sensor(arduino) and then asks for an input from the user for reading data from serial port for a fixed number of times.
The code compiles and runs. However it ignores the line to to take user input from std::cin and keeps running to completion. It doesn't pause to capture data using cin. Each time i ran, the value to be read from cin was set to some junk values like -344969024, -1750564672, 139065363 etc. The code and sample output is as below:
I am on ubuntu 14.04, gcc-4.8.4. This behavior has also been reported at [https://ubuntuforums.org/showthread.php?t=1682452](https://ubuntuforums.org/showthread.php?t=1682452) and is not solved
The code is as below:

```
#include<SerialStream.h>
#include"SerialPort.h"
#include<iostream>
//#include <unistd.h>
//#include <cstdlib>

#include<fstream>
#include<string>

usingnamespaceLibSerial;

int main(int argc,char* argv[])
{

    SerialPort serial_port ("/dev/ttyUSB0");
    serial_port.Open();
    serial_port.SetBaudRate(SerialPort::BAUD_115200 );
    serial_port.SetCharSize(SerialPort::CHAR_SIZE_8 );   

    std::ofstream out("output.txt");

    int i=0;

    for(i=0;i<4;i++)
    {
      std::cout << serial_port.ReadLine();// necessary to read headers from sensor connected to serial port
    }

    serial_port.WriteByte('S');// necessary to initiate the communication from sensor connected to serial port

    int num_readings;    
    std::cout <<"enter number of readings to take"<< std::endl;
    std::cin>>num_readings;
    int j=0;
    while(j<num_readings)
    {
    std::cout << serial_port.ReadLine();
    j++;
    std::cout <<"came inside loop"<< std::endl;
    }

     return0;
}
```

The output is as below:
```
came inside new loop
quat    -0.980.060.16-0.10
came inside new loop
quat    -0.980.060.16-0.10
came inside new loop
quat    -0.980.060.16-0.10
came inside new loop
quat    -0.980.060.16-0.10
came inside new loop
quat    -0.980.060.16-0.10
came inside new loop
quat    -0.980.060.16-0.10
came inside new loop
quat    -0.980.060.16-0.10
came inside new loop
quat    -0.980.060.16-0.10
came inside new loop
quat    -0.980.060.16-0.10
came inside new loop
quat    -0.980.060.16-0.10
came inside new loop
quat    -0.980.060.16-0.10
came inside new loop
quat    -0.980.060.16-0.10
came inside new loop
quat    -0.980.060.16-0.10
came inside new loop
quat    -0.980.060.16-0.10
came inside new loop
quat    -0.980.060.16-0.10
came inside new loop
quat    -0.980.060.16-0.10
came inside new loop
quat    -0.980.060.16-0.10
came inside new loop
quat    -0.980.060.16-0.10
came inside new loop
quat    -0.980.060.16-0.10
came inside new loop
quat    -0.980.060.16-0.10
came inside new loop
quat    -0.980.060.16-0.10
came inside new loop
quat    -0.980.060.16-0.10
```

---

