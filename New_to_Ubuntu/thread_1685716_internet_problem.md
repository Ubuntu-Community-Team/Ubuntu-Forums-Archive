---
title: "internet problem"
date: 2011-02-11
forum: New to Ubuntu
---

### Post by mattc1977 on 2011-02-11
Hello lovely people

I have just installed ubuntu and looking forward to using it.
I have a little problem with connecting to the net.

i am using a wireless connection.
When I click on the connection icon my connection appears and I put in my pass word. first of all it connected but would disconnect me after a short time, so i uninstalled and reinstalled ubuntu and now it wont connect at all although it still shows my connection as being their. I know the wifi is working fine on win 7 as im using it now.
Any ideas?

Matt

---

### Post by mikewhatever on 2011-02-11
Please post the output of **lspci | grep -i network** from a terminal window. This is to show your wireless hardware.

---

### Post by mattc1977 on 2011-02-11
sorry im not sure what you mean by that? Im very much a newbie :redface:

---

### Post by pythoned on 2011-02-11
Hi, it means that you should go in Applications>Accesories>Terminal. Click on it, copy paste the command:
[B]
lspci | grep -i network

[/B]Then copy paste the output the command gave you from the terminal. This command tells us what type of network controller you have. It should be something like Network Controler:........
Post that back here. Good luck!

---

### Post by mattc1977 on 2011-02-11
hi there sorry another problem i cant copy and past as i have to reset comp to go from win 7 (that im on now) to ubuntu.

I have tried to copy it in by hand but it dosnt seem to like the **|** symbol
it says | unexpected token

---

### Post by vivek.pandey on 2011-02-11
you cant use ctrl + c to copy anything from terminal use mouse.click the mouse from the point where you wanna copy drag till where you wanna copy then right click.be sure that you right click the selected area only then click on copy option

---

### Post by mattc1977 on 2011-02-11
yeah but how do i copy paste from win7 to ubuntu?

---

### Post by vivek.pandey on 2011-02-11
> **mattc1977 said:**
> yeah but how do i copy paste from win7 to ubuntu?

you have 2 options for this..
1) copy on some external hard disk and then copy paste back where you want
2)if you want to copy something from win 7 to ubuntu..copy the document in the partition which DOES NOT has ubuntu installed.you can see the contents from ubuntu

but here i guess you need to copy from ubuntu to windows so use a usb pen drive or something as you cant see ubuntu's content from windows :D

---

### Post by mattc1977 on 2011-02-11
ok so i have entered the line of code into the terminal and this is what happens.....


matt@ubuntu:~$ |spci | grep -i network
bash: syntax error near unexpected token `|'
matt@ubuntu:~$

---

### Post by vivek.pandey on 2011-02-11
> **mattc1977 said:**
> ok so i have entered the line of code into the terminal and this is what happens...friend ..


matt@ubuntu:~$ |spci | grep -i network
bash: syntax error near unexpected token `|'
matt@ubuntu:~$

my friend matt the command is 
lspci | grep -i network

the starting character of the command you gave is wrong its not a single bar but l for london

also | is a token and so no command starts with it.so whenever you see it at the beginning of any command check it else you will get a bash error
now copy paste the output of this correct command

---

### Post by mattc1977 on 2011-02-11
ok so the output of the correct command is this. it hasn't really done anything?




matt@ubuntu:~$ lspci | grep -i network
matt@ubuntu:~$

---

### Post by bilallucky on 2011-02-11
im not sure what you mean by that?

---

### Post by mattc1977 on 2011-02-11
well i typed in the command and  it did nothing at all

---

### Post by vivek.pandey on 2011-02-11
> **mattc1977 said:**
> well i typed in the command and  it did nothing at all

i guess you dont have any wireless drivers installed..try this
system->administration->additional drivers->activate any one of the two given wireless drivers,,then run the lspci | grep -i network
and post the ouput

---

### Post by mikewhatever on 2011-02-11
The command wasn't supposed to do anything other then print out the networking hardware in the output. It should have been similar to this:
```
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)
03:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g LP-PHY (rev 01)

```

The lack of output probably means the hardware is not detected. If you have Windows on that computer, check its Device Manager or whatever it's called.

---

### Post by mattc1977 on 2011-02-11
hi mike the device is being detected cuz i can see my connection and other people wifi connections come up it just wont connect.

Neo I followed what you said and i got the message "no proprietary drivers in use on this system"?

---

### Post by vivek.pandey on 2011-02-11
> **mattc1977 said:**
> hi mike the device is being detected cuz i can see my connection and other people wifi connections come up it just wont connect.

Neo I followed what you said and i got the message "no proprietary drivers in use on this system"?

when did you get this error message? did the driver got activated?

---

### Post by mattc1977 on 2011-02-11
there were no drivers to choose from mate

---

### Post by vivek.pandey on 2011-02-11
> **mattc1977 said:**
> there were no drivers to choose from mate

try this system ->administration->synaptic packet manager type broadcam then install the wireless driver from the list..

---

### Post by mattc1977 on 2011-02-11
Hi guys well it seems the reinstall worked im using ubuntu now, although the net speed isnt very fast. but i'll see if i can sort it. if not i'll start a new thread.

Many thanks to you all for your time a help i reallt appreciate it guys, nice one!!!

Matt

---

