---
title: "Xubuntu network connection problem"
date: 2008-12-30
forum: New to Ubuntu
---

### Post by mrkueball on 2008-12-30
Hello. I am new to unix and Ubuntu. I recently loaded Xubuntu on my Dell Latitude CPxJ650gt laptop with no issues. I connected with my network and accessed the internet right away. When I downloaded and installed the 136 updates offered for the OS I lost my ability to connect with my network. I can still "see" my network and most of my neighbors as well, but I cannot connect to it. 

After the updates upon boot I am getting a screen that says the Network Manager Applet needs access to the password for the default keyring. That screen did not come up before the updates. Inputting the password does no good. 

I attempted to check the firewall status with the ufw status command on the terminal, but I get an error message that says I need to be the root to run this script. Could this be the problem?

I have run the following commands in the terminal but I am having trouble getting the mousepad file to a floppy.

iwconfig
ifconfig
nm-tool
sudo lshw -c network
lspci
dmesg|grep ound
dmesg|grep etect

Any help would be apprecitated!!!

---

### Post by wolfen69 on 2008-12-30
you need to type *sudo* in front of any command to become "root" or super user to make changes.

---

### Post by mrkueball on 2008-12-30
Thank you. I know know the firewall is not the problem. Can you help further? I am still having problems getting the output from the terminal to the forum. I've attached it as a word file.

---

### Post by mrkueball on 2008-12-30
Can anyone help please?

---

### Post by dragos_iliescu_2005 on 2008-12-30
If possible, try a wired connection first. Or try wireless with no security/encryption.

---

### Post by Michael.Godawski on 2008-12-30
hi, 

I am just wondering why do you have to entries of the same network with two different names:```

  	 	 	 	 	<!-- 		@page { size: 8.5in 11in; margin: 0.79in } 		P { margin-bottom: 0.08in } 	--> 	  lo        Interface doesn't support scanning.
  
 **wifi0 **    Scan completed :
           Cell 01 - Address: 00:18:01:EA:BD:4A
                     ESSID:"1Y242"
                     Mode:Master
                     Frequency:2.462 GHz (Channel 11)
                     Signal level=-36 dBm  Noise level=-93 dBm
                     Encryption key:on
                     Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                     Extra:bcn_int=100
                     Extra:resp_rate=10
           Cell 02 - Address: 00:1F:90:E3:3C:67
                     ESSID:"GJG90"
                     Mode:Master
                     Frequency:2.462 GHz (Channel 11)
                     Signal level=-85 dBm  Noise level=-93 dBm
                     Encryption key:on
                     Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                     Extra:bcn_int=100
                     Extra:resp_rate=10
  
 **wlan0 **    Scan completed :
           Cell 01 - Address: 00:18:01:EA:BD:4A
                     ESSID:"1Y242"
                     Mode:Master
                     Frequency:2.462 GHz (Channel 11)
                     Signal level=-35 dBm  Noise level=-94 dBm
                     Encryption key:on
                     Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                     Extra:bcn_int=100
                     Extra:resp_rate=10
 
```

Can you please post your interfaces?
```

cat /etc/network/interfaces
```

---

### Post by mrkueball on 2008-12-30
Command output

john@Johns-laptop:~S cat /ect/network/interfaces
auto lo
iface lo inet loopback

Thank you!

---

### Post by mrkueball on 2008-12-30
Thank you all for your help so far. Can anyone please provide more information to help me solve this network connection problem?

---

