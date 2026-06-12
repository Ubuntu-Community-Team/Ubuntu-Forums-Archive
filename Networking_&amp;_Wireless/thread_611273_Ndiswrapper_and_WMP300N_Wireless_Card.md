---
title: "Ndiswrapper and WMP300N Wireless Card"
date: 2007-11-12
forum: Networking &amp; Wireless
---

### Post by diggity801 on 2007-11-12
I know you have had a million of these threads but I can't find one with my problem.

Ok so I installed Ubuntu and I thought I would go to the help page to find Ndiswrapper. So I find a page that says "Using Windows Wireless Drivers"

1. Obtain the windows Driver for your system and locate the file that ends with .inf
2. Install ndisgtk (System > Administration > Synaptic Package MAnager). 


I'll just stop with number two because there is NO ndisgtk in the Synaptic Package Manager. So i'm kinda peeved that the instructions are completely wrong in this regard. Can someone explain to me why this is? And how I can fix it?

---

### Post by reckless2k2 on 2007-11-12
ok.....here we go......

[LIST=1]
[*]1 - you have to enable extra repos to get ndisgtk
[*]2 - you have to install a few more packages prior to using ndisgtk anyway
[*]3 - i'll give you the command line install
[/LIST]

start synaptic and install the following:

[LIST]
[*]ndiswrapper -utils-1.9
[*]ndiswrapper-common
[/LIST]

if you don't have an internet connection, those 2 packages come right off the install CD. make sure you have it in the drive if you don't have internet connection. 

now grab the .inf AND .sys that corresponds to your device. i will not go into the "finding" details since i assume you know them. you MUST HAVE THE INF AND SYS files in order for it to work. 

copy these files to you home directory. after the ndis packages i spoke about above have been added, then fire up the terminal. 

THIS IS THE QUICK AND DIRTY

with the inf and sys in the home directory, this adds the driver
```
sudo ndiswrapper -i THEFILE.inf
```

this verifies it's installed. it should say PRESENT. if it does not, check the location of you drivers
```
sudo ndiswrapper -l
```

```
sudo depmod -a
```

```
sudo modprobe ndiswrapper
```

this inserts ndis mod
```
sudo ndiswrapper -m
```

now you need to do one more thing so you never have to do this again after each boot. you need to edit the modules file to make sure ndiswrapper starts at boot:

```
gksudo gedit /etc/modules
```
the bottom of this file add "ndiswrapper" without quotes. save the file.

now if you open the network manager you will have wlan0. set it up for your network. deactivate the wired card and you'll be golden. 

thanks.....no applause just money... hahahaha

---

