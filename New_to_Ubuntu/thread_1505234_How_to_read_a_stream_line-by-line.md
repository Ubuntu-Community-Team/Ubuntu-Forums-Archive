---
title: "How to read a stream line-by-line?"
date: 2010-06-08
forum: New to Ubuntu
---

### Post by outleradam on 2010-06-08
I have a problem with a script I am writing.  This script communicates across a serial port to my car's computer.   Basically, what I want it to do is to 
1. Take user input from a read statement, then transfer it to the serial port "/dev/rfcomm0".  #This works 
2. Then upon transmission from the serial port, put that information into a variable and process it. #This dosn't work
3. repeat

My problem is How I'm receiving information.  How can I possibly use the "cat" statement to keep the port open, while processing the output of cat line-by-line?

The problem is all located in the function mainLoop ()

```
#! /bin/bash

####set up variables####
myObdDeviceMAC=00:0D:18:B1:09:DA 
myObdComPort="/dev/rfcomm0"
exitNext=""

####sudo check####
if [ "$(id -u)" != "0" ]; then
    echo "You do not have sufficient privlidges to run this script. Try again with sudo configure"
    exit 1
fi

#ExitPoint provides a way out of the program in the event of error if the exitNext variable is set.
ExitPoint () {
test exitNext = 1 && echo "Could not connect to Serial Device, possible causes are bad communication or no connection"
test exitNext = 2 && echo "please install package bluez-utils"
echo "$exitNext"
test "$exitNext" != "" && exit $exitNext
}

#checkDepends verifies packages are in place
checkDepends() {
echo "Checking Dependencies"
test `which hcitool`>/dev/null || exitNext=2
ExitPoint
echo "Dependencies Met"

#prepCom prepares the com port by initializing the bluetooth device and the serial port
prepCom () {
#initialize port
echo "Initializing Com Port"
hcitool cc $myObdDeviceMAC &&  hcitool auth $myObdDeviceMAC || exitNext=1
ExitPoint
#connect to port
rfcomm connect 0 &
#prepare port for data communications
sleep 1
stty -F "$myObdComPort" speed 9600 ignbrk -brkint -icrnl -imaxbel -opost -onlcr -isig -icanon -iexten -echo -echoe -echok echoctl -echoke time 5 min 1 line 0
}

mainLoop () {
cat /dev/rfcomm0 &
echo Entering read loop
while [ 1 ]
do 
 read userinput 
 echo -e ${userinput}"\r\n"| sudo tee "$myObdComPort" 
done

}


####Controlling Code####
#Check Dependencies
checkDepends
#Prepare communications
prepCom
mainLoop
exitNext=0
ExitPoint

```Currently, I am reading the information from the cat command, and I don't know how to process it.  When I receive "41" back, that means it is a response, then the rest of the charactors on that line need to be processed.  I don't know how to isolate the information I need and put it into a variable.   I just can't figure it out, how can I process this information?
If there is another way to do it, please let me know.  Basically, I've created a input and output system that is it's own terminal.  I just need to process it line-by-line.


Any help with processing information line-by-line from the cat, or equivalent command is needed.

---

### Post by outleradam on 2010-06-08
Oh, yeah, I forgot to mention..  At the end of each transmission the device returns a ">" asking for more input.   This should signal end of line.  Now how to take everything beween the last > and the next > and put it into a variable is my question.

---

### Post by outleradam on 2010-06-09
Still need help with chopping up this stream.  I receive a ">" from the device and that means it's ready for more input.  I need to be able to monitor the stream and place it into a variable, then when I receive a ">" it should stop.

---

### Post by outleradam on 2010-06-09
anyone?  How can I chop a stream into a variable upon receipt of the charactor ">"

---

### Post by outleradam on 2010-06-13
This program will initiate a serial connection, hold it open and read from the device
```

#! /bin/bash
#Reuse this code as you like.  Props go to me, Adam Outler.

#Set up device variables
myObdDeviceMAC=00:0D:18:B1:09:DA 
myObdComPort="/dev/rfcomm0"
exitNext=""

####sudo check####
if [ "$(id -u)" != "0" ]; then
    echo "You do not have sufficient privlidges to run this script. Try again with sudo configure"
    exit 1
fi

#ExitPoint provides a way out of the program in the event of error if the exitNext variable is set.
ExitPoint () {
    test exitNext = 1 && echo "Could not connect to Serial Device, possible causes are bad communication or no connection"
    test exitNext = 2 && echo "please install package bluez-utils"
    echo "$exitNext"
    test "$exitNext" != "" && exit $exitNext
}

#checkDepends verifies packages are in place
checkDepends() {
    echo "Checking Dependencies"
    test `which hcitool`>/dev/null || exitNext=2
    ExitPoint
    echo "Dependencies Met"
}

#prepCom prepares the com port by initializing the bluetooth device and the serial port
prepCom () {
#initialize port
    echo "Initializing Com Port"
    hcitool cc $myObdDeviceMAC 2>&1 /dev/null &&  hcitool auth $myObdDeviceMAC 2>&1 /dev/null || exitNext=1
    ExitPoint
#connect to port
    echo "Connecting rfcomm port to ELM device"
    rfcomm connect 0 &
#prepare port for data communications
    echo "Waiting 2 seconds for connection."
    sleep 2
    echo "Setting port specs"
    stty -F "$myObdComPort" speed 9600 ignbrk -raw -brkint -icrnl -imaxbel -opost -onlcr -isig -icanon -iexten -echo -echoe -echok echoctl -echoke time 5 min 1 line 0
    echo "Linking $myObdComPort to /dev/obd"
    test ! -L "/dev/obd" && ln -s "$myObdComPort" /dev/obd
}

mainLoop () {
#mainLoop will read 1 charactor at a time until it sees ">", then it will display the cooked data and let the user input his/her data.

    echo "Opening /dev/obd port for writing"
     echo "type '!quit' to exit"
     userinput="atz"

#Infinate Loop until !quit is entered by user
     while [ 1 ]
     do 
         echo -e ${userinput}"\r\n" > "/dev/obd" 
          counter=0
#Read from port until > loop
            while read -n1 CHAR 
          do
                if [ "$CHAR" != ">" ]; then
                      mydata=$mydata$CHAR
                else 
                        break
                fi  
          done < /dev/obd
#Cook OBD data to human readable
    OBDDATA=${OBDDATA:$beginstring:999}
     OBDDATA=`echo $mydata|sed s/"^M"/"\n"/g| tr -d "[:cntrl:]"`
      echo "$OBDDATA"
#Read line and then process to OBD unit
     read -p "$CHAR" userinput
     beginstring=${#char}
    echo -e ${userinput}"\r\n" > "/dev/obd"
#Pause for a reset
     test "$userinput" = "atz" && sleep 5
#Exit on a user !quit
     test "$userinput" = "!quit" && exitNext=0 && ExitPoint
     sleep .5 
     mydata=""
    done
}

#Check Dependencies
checkDepends
#Prepare communications
prepCom
#Main I/O loop
mainLoop
#In case the program randomly exits the read loop
exitNext=0
ExitPoint

```

---

