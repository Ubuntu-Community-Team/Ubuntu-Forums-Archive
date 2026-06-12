---
title: "Keeping a serial port opened and functional?"
date: 2010-07-16
forum: New to Ubuntu
---

### Post by outleradam on 2010-07-16
I have a serial connection set up through bluetooth to my car.  I run a script after pairing the device to set up the /dev/rfcomm0 device.   This requires a script to be run every time.  

1. Is there a way I can bypass the script and just have it set up automatically?  
2. I would like this script to somehow be run and check to see if it is connected and if it is not, check to see if the device is paired, and then reconnect.   
3. I would like to bypass having to enter a password.
4.  I would like it to be MAC address independent.  

Here is the script which is required to initialize the comm port.

```
adam@adam-desktop:~$ cat ./obd2ner
#! /bin/bash

####sudo check####
if [ "$(id -u)" != "0" ]; then
    echo "You do not have sufficient privlidges to run this script. Try again with sudo configure"
    exit 1
fi



####set up devices####
myDeviceMAC=00:0D:18:B1:09:DA 
myComPort="/dev/rfcomm0"
exitNext=""


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
hcitool cc $myDeviceMAC 2>&1 /dev/null &&  hcitool auth $myDeviceMAC 2>&1 /dev/null || exitNext=1
ExitPoint
#connect to port
echo "Connecting"
rfcomm connect 0 &
#prepare port for data communications
echo "Waiting 2 seconds for connection."
sleep 2
echo "Setting port specs"
stty -F "$myComPort" speed 9600 ignbrk -raw -brkint -icrnl -imaxbel -opost -onlcr -isig -icanon -iexten -echo -echoe -echok echoctl -echoke time 5 min 1 line 0
echo "Linking $myComPort to /dev/comPort"
test ! -s "/dev/obd" && ln -s "$myComPort" /dev/comPort
}


mainLoop () {

 echo "Opening /dev/comPort port for writing"
 #cat -A /dev/comPort  &
 

 echo "console active.  press ctrl+c to exit>"
 while [ 1 ]
 do 
  read userinput 
  echo -e ${userinput}"\r" > $myComPort 
  
  #DATA="`xxd -ps -l 1 "$myComPort" `"
  #echo $DATA
 done

}


#Check Dependencies
checkDepends
#Prepare communications
prepCom
mainLoop

exitNext=0
ExitPoint



```

This seems excessive and as soon as the script is closed, the com port is shut down.  Is there an eaiser way to obtain any of the goals above?

---

### Post by outleradam on 2010-07-18
HELP!!!!

Isn't there a system method for bluetooth com ports?

---

