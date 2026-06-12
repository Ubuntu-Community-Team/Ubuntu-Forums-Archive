---
title: "Need help getting a D-Link wireless card to work in 7.10"
date: 2008-03-29
forum: Networking &amp; Wireless
---

### Post by stromdal on 2008-03-29
I am new to Linux and need help getting a D-Link DWL-G520M wireless NIC to work in Ubuntu 7.10. I checked the [https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsDlink](https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsDlink) list, but the card isn't in there, so I followed the general recommendations I found and installed "ndiswrapper" using "Install and Remove Applications". I downloaded the latest Windows drivers from D-Link: [http://www.dlink.com/products/support.asp?pid=422&sec=0#drivers](http://www.dlink.com/products/support.asp?pid=422&sec=0#drivers)

Here is where i messed up: I only unzipped the inf file before installing the driver:

user@localhost:~/Desktop$ sudo ndiswrapper -i net5513.inf 
installing net5513 ...
couldn't find "ar5513.sys" in "."; make sure all driver files, including .inf, .sys (and any firmware files) are in "." -
installation may be incomplete
forcing parameter MapRegisters from 256 to 64
forcing parameter MapRegisters from 256 to 64
couldn't find "ar5513.sys" in "."; make sure all driver files, including .inf, .sys (and any firmware files) are in "." -
installation may be incomplete
forcing parameter MapRegisters from 256 to 64
forcing parameter MapRegisters from 256 to 64

Unzipping the rest of the files and reinstalling the driver didn't help and I can't uninstall the driver:

user@localhost:~/Desktop$ sudo ndiswrapper -i net5513.inf 
driver net5513 is already installed
user@localhost:~/Desktop$ sudo ndiswrapper -l
net5513 : invalid driver!
user@localhost:~/Desktop$ sudo ndiswrapper -r net5513.inf 
couldn't delete /etc/ndiswrapper/net5513.inf: Filen eller katalogen finns inte

How do I clean up this mess?

regards
/stromdal

---

### Post by dstew on 2008-03-29
The removal command should be either```
sudo ndiswrapper -r net5513
```or```
sudo ndiswrapper -e net5513
```That is, no .inf after the name. If you do```
ndiswrapper --help
```it will tell you to use -r or -e to remove the driver. It depends on the version.

---

### Post by stromdal on 2008-04-04
Thanks, that solved the problem. I still haven't figured out the proper procedure for getting my WLAN card to work, but that's a question for another thread, I guess.

Regards
/stromdal

---

### Post by dstew on 2008-04-04
Well, I think we can continue this thread, it's all the same problem. You want to get your card to work, if possible.

> user@localhost:~/Desktop$ sudo ndiswrapper -i net5513.inf
installing net5513 ...
couldn't find "ar5513.sys" in "."; make sure all driver files, including .inf, .sys (and any firmware files) are in "." -
installation may be incompleteHere is your first problem. You need to have the .inf, .sys and any other driver files in the same directory in order for ndiswrapper to create a valid driver. The .inf file is the "information" file. It is only a text file that runs the driver configuration. The actual driver is the .sys file.

---

