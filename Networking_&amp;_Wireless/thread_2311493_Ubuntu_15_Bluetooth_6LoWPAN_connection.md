---
title: "Ubuntu 15 Bluetooth 6LoWPAN connection"
date: 2016-01-27
forum: Networking &amp; Wireless
---

### Post by hoffman-jon on 2016-01-27
I am trying to establish a Bluetooth Smart (LE) connection between two Linux devices where I can use IPSP (Internet Protocol Support Profile) with 6LoWPAN so I can communicate between the two devices using IPv6 over the Bluetooth Smart (LE) connection.  The connection would have the following two devices:
[LIST]
[*]Slave:  The slave would be advertising the service 
[*]Master:  The master would scan for the slave and once found it would connect to it 
[/LIST]

I have attempted this connection with several Linux distributions/devices with some success.  If the slave device is running Ubuntu 14.04 with Bluez 4.101 I am able to establish the connection from several different devices running various kernels/Bluez versions without any problems.  I am using the 3.19 kernel on the Ubuntu 14.04 box that I downloaded from:  [URL="http://kernel.ubuntu.com/~kernel-ppa/mainline/linux-3.19.y.z-queue/2016-01-07-vivid/"]http://kernel.ubuntu.com/~kernel-ppa/mainline/linux-3.19.y.z-queue/2016-01-07-vivid/
[/URL]
The following command sequence establishes the 6LoWPAN connection:
Slave:
```
modprobe Bluetooth_6lowpan                         //Install module
echo 35 > /sys/kernel/debug/bluetooth/6lowpan_psm   //Enable 6LoWPAN
hciconfig hci0 leadv                                                //Advertise Service
```
 
Master:
```
modprobe Bluetooth_6lowpan                                               //Install module
echo 1 > /sys/kernel/debug/bluetooth/6lowpan_enable  //Enable 6LoWPAN
hcitool lecc 5c:f3:70:xx:xx:xx                                                    //Connect to service
echo “connect 5c:f3:70:xx:xx:xx 1” > /sys/kernel/debug/bluetooth/6lowpan_contol   //Make connection
```

This procedure consistently works and we are able to access web services between the two machines over the Bluetooth Smart (LE) connection.  Once the last command is run on the Master device, both the master and slave have bt0 network devices that we can configure and use for the communication.  The problem is we do not want to use Bluez 4 or the older kernel on the slave device.

Once I upgrade the slave device to Ubuntu 15.10 using BlueZ 5.35 and the 4.2 kernel (standard Ubuntu 15.10 setup) I am not able to establish the 6LoWPAN connection between that slave and any device acting as the master.  This is not unique to Ubuntu, the connection fails for any slave that runs a 4.X kernel with Bluez 5 (Ubuntu 15, Fedora 23 or Raspberry Pi).  The procedure that I use to establish the connection is the same as the one listed above except I replace the “echo 35 > /sys/kernel/debug/bluetooth/6lowpan_psm “ line on the slave with this line “echo 1 > /sys/kernel/debug/bluetooth/6lowpan_enable”.

With Ubuntu 15 (or any distribution with the 4.x kernel and Bluez 5) once the last command is run on the master, the bt0 device is automatically brought up on the master however the bt0 device is not brought up on the slave.  In 30 to 40 seconds the master automatically disconnects and the bt0 device is brought down on the master.  I am thinking that I may need an additional step on the slave device to tell it to bring up the 6lowpan connection however I cannot find anything on the Internet.

I have posted this question to the Bluez mailing list but the solution seems to work for them however I am unsure what kernel or bluez version they are using or how their kernel is configured (I did ask the question).  I have also posted the question to super user a couple weeks ago and have not received any replies.  Has anyone successfully established a 6LoWPAN connection between two devices running Ubuntu 15 with Bluez5?  I have been beating my head against the wall for a couple of weeks on this so any help, pointers, ideas, suggestions, well wishes, prayers, alcohol or sympathy would be greatly appreciated.

I do have full hcidump traces for both the successful and failed attempts.  I also have full wireshark dumps of the success and failed connection if anyone would like to see them.

---

### Post by hoffman-jon on 2016-01-29
Solution


I Just solved the issue.  the problem was with the kernel.  I installed Ubuntu 15 but had the same issue as the Raspberry Pis so I downloaded the source for the 4.4 kernel, configured it and built a new kernel.  Once the new kernel was in place everything worked great.  Not sure if it was the patch level of the kernel or the configuration but it is now working.

---

