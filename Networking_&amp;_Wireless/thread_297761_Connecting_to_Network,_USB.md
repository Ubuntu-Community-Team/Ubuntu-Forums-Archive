---
title: "Connecting to Network, USB"
date: 2006-11-11
forum: Networking &amp; Wireless
---

### Post by Chouca on 2006-11-11
Hi,

I have installed Dapper and is very close to get my DEll Wireless 1450 USB card working (ndiswrapper and orig driver) but...I can see my and my neighbors networks but can not get connected or even confifure correctly by GUI or CLI.


Trying to configure manually gives this result;

```
martin@ubuntu:~$ sudo iwconfig wlan0 essid wireless_235 ap 00:90:4B:E2:9E:88
martin@ubuntu:~$ iwconfig
lo        no wireless extensions.

wlan0     IEEE 802.11g  ESSID:off/any
          Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated
          Bit Rate:2 Mb/s   Tx-Power:17 dBm
          RTS thr:2347 B   Fragment thr:2346 B
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```


But the networks are there and the card detects them...


```
martin@ubuntu:~$ iwlist wlan0 scan
wlan0     Scan completed :
          Cell 01 - Address: 00:90:4B:E2:9E:88
                    ESSID:"wireless_235"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.472 GHz (Channel 13)
                    Quality:0/100  Signal level:-50 dBm  Noise level:-256 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=1
```



If I remove all wlan0 information in etc/network/interfaces I can enter the info by CLI once (sometimes) - but as soon 
as I try the Network Manager it seems to be erased and the result is as above....


Any ideas - my grey hair is turning white...

Regards

Martin

---

### Post by FrodoB on 2006-11-11
You need to make a little script can call it test.sh and put the following into it:

#!/bin/sh
/usr/bin/sudo /sbin/iwconfig wlan0 mode "Managed"
/usr/bin/sudo /sbin/iwconfig wlan0 key "XXXXXXXXXXXXXXXXXXXXXXXXXX"
/usr/bin/sudo /sbin/iwconfig wlan0 essid "wireless_235"
/usr/bin/sudo /sbin/dhclient wlan0

Modify the key to be the hex value of the key from Xs to that your access point uses or if you only know the ASCII equivalent then put it in as: (note I am using 128bit (104bit) wep examples.

/usr/bin/sudo /sbin/iwconfig wlan0 key "s:XXXXXXXXXXXXX"

instead.

Save it and change the permissions to:

$ chmod 755 test.sh

then run it:

$ ./test.sh

run iwconfig and hopefully all will be good and then check netstat -rn. Post the results to the group.

---

### Post by Chouca on 2006-11-12
Thanks FrodoB,

I copied your script and stored it in my home folder.

When I tried to run it WITH the first line #!/bin/sh in the scrip I got;

```
martin@ubuntu:~$ chmod 755 test.sh
martin@ubuntu:~$ ./test.sh
bash: ./test.sh: /bin/sh^M: bad interpreter: No such file or directory
```

So, I removed #!/bin/sh and then run it again, this is what happened;

```
martin@ubuntu:~$ chmod 755 test.sh
martin@ubuntu:~$ ./test.sh
Error for wireless request "Set Encode" (8B2A) :
    SET failed on device wlan0 ; Invalid argument.
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/products/DHCP

Listening on LPF/wlan0/00:90:4b:fb:f3:71
Sending on   LPF/wlan0/00:90:4b:fb:f3:71
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 19
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 17
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 11
No DHCPOFFERS received.
No working leases in persistent database - sleeping.


martin@ubuntu:~$ iwconfig
lo        no wireless extensions.

sit0      no wireless extensions.

wlan0     IEEE 802.11g  ESSID:off/any
          Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated
          Bit Rate:2 Mb/s   Tx-Power:21 dBm
          RTS thr:2347 B   Fragment thr:2346 B
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

martin@ubuntu:~$ netstat -rn
Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
```



Still - when I scan I see two networks - one is mine and one is my neighbors...


Regards

Martin

---

### Post by FrodoB on 2006-11-12
The ^M means that you have a dos/windows text format for some reason. Did you use gedit to make the test file:

Applications --> Text Editor

Also did you change the key to your access point's value?

Here it is again with a sleep added to allow for settling time: ( I did test it no my system with my keys and essid and it did work .:) )

#!/bin/sh
/usr/bin/sudo /sbin/iwconfig wlan0 mode "Managed"
/usr/bin/sudo /sbin/iwconfig wlan0 key "xxxxxxxxxxxxxxxxxxxxxxxxxx"
/usr/bin/sudo /sbin/iwconfig wlan0 essid "wireless_235"
/bin/sleep 5
/usr/bin/sudo /sbin/dhclient wlan0

---

### Post by Chouca on 2006-11-12
Thanks FrodoB,

Changed the saved format to UTF-8

Now I get;

root@ubuntu:~# chmod 755 test.sh
root@ubuntu:~# ./test.sh
bash: ./test.sh: cannot execute binary file

](*,)  


Regards

Martin

---

### Post by FrodoB on 2006-11-12
Martin;

Go to a command prompt and cat the file and copy and paste the output so I can see it:

$ cat test.sh

---

### Post by Chouca on 2006-11-12
Thanks for your patience Frodo,

Something had happened with the # character in the XP to Linux transport by USB memory stick....:p 

This is how it looks now;

```
martin@ubuntu:~$ cat test.sh
#!/bin/sh
/usr/bin/sudo /sbin/iwconfig wlan0 mode "Managed"
/usr/bin/sudo /sbin/iwconfig wlan0 key "s:67xxxxxx4D"
/usr/bin/sudo /sbin/iwconfig wlan0 essid "wixxxxx_235"
/bin/sleep 5
/usr/bin/sudo /sbin/dhclient wlan0
martin@ubuntu:~$
martin@ubuntu:~$ chmod 755 test.sh
martin@ubuntu:~$ ./test.sh
Error for wireless request "Set Encode" (8B2A) :
    SET failed on device wlan0 ; Invalid argument.
/bin/sleep: invalid time interval `5\r'
Try `/bin/sleep --help' for more information.
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/products/DHCP

Listening on LPF/wlan0/00:90:4b:fb:f3:71
Sending on   LPF/wlan0/00:90:4b:fb:f3:71
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 4
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
martin@ubuntu:~$ iwconfig
lo        no wireless extensions.

sit0      no wireless extensions.

wlan0     IEEE 802.11g  ESSID:off/any
          Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated
          Bit Rate:2 Mb/s   Tx-Power:12 dBm
          RTS thr:2347 B   Fragment thr:2346 B
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```


Regards

Martin

---

### Post by FrodoB on 2006-11-12
Your wep key looks invalid. It should be 13 characters for ASCII or 26 for Hex.

ASCII:
/usr/bin/sudo /sbin/iwconfig wlan0 key "s:XXXXXXXXXXXXX"

Hex:
/usr/bin/sudo /sbin/iwconfig wlan0 key "XXXXXXXXXXXXXXXXXXXXXXXXXX"

Note the s: that begins an ASCII key.

Generate new keys and put them in the access point and Ubuntu perhaps:

[http://www.andrewscompanies.com/tools/wep.asp](http://www.andrewscompanies.com/tools/wep.asp)

I am using 128 bit examples.

---

### Post by Chouca on 2006-11-12
Guess what Frodo,

I am now replying from Dapper Wireless with the Dell Wireless 1450 USB card!!!!:D :D :D 

THANKS so much for all your help, the final piece of the puzzle was the wep key!

Now is the question  do I dare  to shutdown the computer -  will I ever get it up again:-? 

Thanks again!

Martin

---

### Post by FrodoB on 2006-11-12
Yes please do it now and reply back so we know. The keys can be difficult now and then.

---

### Post by Chouca on 2006-11-12
Hi again Frodo,

When i shutdown or suspend the wireless netork does not go up automatically but I can get the network up by running your excellent script. 

I have disabled everything in etc/network/interfaces while trying to get things going... 

```
#iface wlan0 inet dhcp
#wireless-essid wireless_235
#wireless-key s:XXXXXXXXXX

#auto wlan0
```


is that the place to enable some of them to obtain "auto-start" or what is the best place to auto-run the commands from the script?


Regards

Martin

---

### Post by FrodoB on 2006-11-12
If you get the key that works in the script into the interfaces file along with the ESSID it should just startup and work when you boot or manually at a prompt:

$ sudo ifup wlan0

$ sudo ifdown wlan0

if the ifup approach works then it should work at reboot as well.

---

### Post by Chouca on 2006-11-13
Hi,


1.

If I edit the interfaces file like this - it does not work (again I do not really know what I amk doing  :-?) ;

```
auto lo
iface lo inet loopback



iface eth0 inet dhcp

auto eth0

/usr/bin/sudo /sbin/iwconfig wlan0 mode "Managed"

/usr/bin/sudo /sbin/iwconfig wlan0 key "s:XXXX-XXXX-XX"

/usr/bin/sudo /sbin/iwconfig wlan0 essid "wireless_235"

# /bin/sleep 5

/usr/bin/sudo /sbin/dhclient wlan0

```



2.

The script itself test.sh runs great in the dhcp part of the script I get a question;

```
"The applet 'nm-applet'wants access to the keyring but is locked.

Password:
```

I have entered and confirmed a new password and everything works then OK.


Regards

Martin

---

### Post by FrodoB on 2006-11-13
Martin;

Your interfaces file needs have the wlan0 section replaced with this, but you need to get the Hex equivalent of your wep key:


iface wlan0 inet dhcp
wireless-essid wireless_235
wireless-key xxxxxxxxxxxxxxxxxxxxxxxxxx
auto wlan0

You can get the equivalent at this site:

[http://www.andrewscompanies.com/tools/wep.asp](http://www.andrewscompanies.com/tools/wep.asp)

The have a section that can take your key: "Custom Phrase" and then you click on "Generate Custom Key" and it give the exact phrase that you entered and its Hex equivalent underneath. Get this hex version and put it into the "wireless-key" in your interfaces file in place of the xxxxxxxxxxxxxxxxxxxxxxxxxx

That should come up on reboot.

Let me know how it goes.

---

### Post by Chouca on 2006-11-13
Hi Frodo,

Tried with the proposed lineds in Interfaces - but with no Improvement.

iwconfig shows;

```
martin@ubuntu:~$ iwconfig
lo        no wireless extensions.

sit0      no wireless extensions.

wlan0     IEEE 802.11g  ESSID:off/any
          Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated
          Bit Rate:2 Mb/s   Tx-Power:12 dBm
          RTS thr:2347 B   Fragment thr:2346 B
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```


In the (working) script I have the key in format:
/usr/bin/sudo /sbin/iwconfig wlan0 key "s:XXXX-XXXX-XX"

and that seem to work - but that is 10 or 12 characters (depending if you count the "-") so I dont get a "match" with the needed 13 characters in the code  tranformer:-? 

Regards

Martin

---

### Post by FrodoB on 2006-11-13
Well whatever key works in the script needs to go into interfaces exactly as it did in the working script but after the key work wireless key

wireless-key s:xxxxxxxxxxxx

If the dashes were required in the one they should be in the other.

---

### Post by digivore on 2006-11-13
Hi, I have been reading over the post, and i don't know if all the encryption stuff is my answer.  But i have a WUSB11 nic, and the driver is loaded because it can view routers, but i consistantly get the 'connection failed' error message when i try to connect to my router, or my neighbors router. Both do not have encryption.  I had this working in Dapper, but recently fresh installed edgy.  Now i can't figure it out.   any ideas?

---

### Post by FrodoB on 2006-11-13
Please start a new thread on this topic.  Please provide outputs from:

iwlist wlan0 scanning

or replace wlan0 with the name of your device.

Also give an output from:

iwconfig

I don't want to get two problems in the same thread. It hides on problem and makes reading about the other confusing.

Thanks,

FrodoB

---

### Post by Chouca on 2006-11-13
> Well whatever key works in the script needs to go into interfaces exactly as it did in the working script but after the key work wireless key

wireless-key s:xxxxxxxxxxxx

If the dashes were required in the one they should be in the other.


Sorry to say it did not work with the same key in  "Interfaces"  as in the script.

It seems like the script is magic :o ...

I guess there is a way to start the script at the end of the boot sequence???


Martin

---

### Post by FrodoB on 2006-11-13
Put the working commands into:

/etc/rc.local

it gets run at the end of startup.

# By default this script does nothing.

# You command go before the exit 0 which must be left alone


exit 0

---

### Post by Chouca on 2006-11-13
Works lika a charm!

The only remaining "hickup" is that I have to enter a Keyring password but apart from  that it runs beautiful!

In /etc/rc.local I did  enter;

```
/usr/bin/sudo /sbin/iwconfig wlan0 mode "Managed"

/usr/bin/sudo /sbin/iwconfig wlan0 key "s:xxxx-xxxx-xx"

/usr/bin/sudo /sbin/iwconfig wlan0 essid "wireless_235"
exit 0
```


and thanks to your skill and helpfulness IT WORKS!!!


Any ideas to omit the Keyring PW?


Thanks!

Martin

---

