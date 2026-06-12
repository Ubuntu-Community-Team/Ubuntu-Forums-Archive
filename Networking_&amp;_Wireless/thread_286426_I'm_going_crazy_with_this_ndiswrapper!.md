---
title: "I'm going crazy with this ndiswrapper!"
date: 2006-10-27
forum: Networking &amp; Wireless
---

### Post by maddbaron on 2006-10-27
Ok I downloaded it from a person on this board, cool. I moved over my laptop's drivers to my desktop. check. I unzipped the ndiswrapper to desktop from the tar.gz file. opened konsole tried to set it up and got cannot find...what on earth do I do now? it said it couldnt find my bcw15.inf and its RIGHT on the desktop...

I am not at all good at coding, I just use what I find here and automatix and adept and now even those arent working for me, adept has ndiswrapper but it says apt error.

Can anyone, someone please help me???

I still have the tar.gz on my desktop, still have the unzipped folder of it on my desktop and the broadcom drivers too.

I dont know what to enter in konsole to get them in my system, only thing i managed to do was blacklist the driver I dont need according to a guide I found here but whenever I try sudo modprobe or whatever i see in the guard it doesnt work.

Can someone please help me?????


ndiswrapper on desktop is 1.27

> cd '/home/maddbaron/Desktop'
maddbaron@baronworks:~$ cd '/home/maddbaron/Desktop'
maddbaron@baronworks:~/Desktop$ sudo ndiswrapper -i ~/home/maddbaron/desktop/bcwl5/bcwl5.inf
Password:
sudo: ndiswrapper: command not found
maddbaron@baronworks:~/Desktop$ sudo ndiswrapper -1.27 ~/home/maddbaron/desktop/bcwl5/bcwl5.inf
sudo: ndiswrapper: command not found

---

### Post by squibT on 2006-10-27
Really...!

There is a ton of info on this forum with solutions to your problem. Try the search button....

You dont say what version of Ubuntu you are using....you are also not in the drivers directory when executing your command.

Why install ndiswrapper from somewhere else when the it is present on your software...SP Manager

Try this:

[http://www.ubuntuforums.org/showthread.php?t=285712](http://www.ubuntuforums.org/showthread.php?t=285712)

---

### Post by DJ Scribblinni on 2006-10-27
The folder Desktop has a capital D in it.  **Linux is case sensitive.**  See what happens when you try it this way. ```
sudo ndiswrapper -i ~/home/maddbaron/Desktop/bcwl5/bcwl5.inf
```
Assuming that bcwl5 is all lowercase...

---

### Post by maddbaron on 2006-10-27
I am using Kubuntu Edgy and I have been searching. I tried adding it through automatix and I keep getting errors in fact a lot of stuff I downloaded while in dapper seem not to work in edgy.

I dont understand this output
> 
maddbaron@baronworks:~$ sudo ndiswrapper -i /home/maddbaron/desktop/bcwl5.inf
Installing bcwl5
cp: cannot stat `/home/maddbaron/desktop/bcwl5.inf': No such file or directory
maddbaron@baronworks:~$ sudo ndiswrapper -i ~/home/maddbaron/desktop/bcwl5/bcwl5.inf
bcwl5 is already installed. Use -e to remove it
maddbaron@baronworks:~$ sudo ndiswrapper -l
Installed ndis drivers:
bcwl5   invalid driver!

How is invalid if its already in use?

---

### Post by maddbaron on 2006-10-27
how can I fix this invald driver?

---

### Post by squibT on 2006-10-27
Try this and post the output:

sudo ndiswrapper -l
You should get driver installed, hardware present

---

### Post by nyinge on 2006-10-27
Maddbaron,

You're mispelling the word "Desktop".  It's uppercase "D".

So, it's gonna go something like:
```

sudo ndiswrapper -i /home/maddbaron/Desktop/bcwl5.inf

```
... assuming your inf file is on your desktop.

Edit:  Unless you've changed the name of your "Desktop" folder to "desktop," of course.

---

### Post by maddbaron on 2006-10-27
maddbaron@baronworks:~$ sudo ndiswrapper -l
Installed ndis drivers:
bcwl5   invalid driver!

---

### Post by nyinge on 2006-10-27
Try installing it again with the "Desktop" fix, k?  And print out the result like squibT said.

---

### Post by maddbaron on 2006-10-27
> **nyinge said:**
> Maddbaron,

You're mispelling the word "Desktop".  It's uppercase "D".

So, it's gonna go something like:
```

sudo ndiswrapper -i /home/maddbaron/Desktop/bcwl5.inf

```
... assuming your inf file is on your desktop.

Edit:  Unless you've changed the name of your "Desktop" folder to "desktop," of course.

maddbaron@baronworks:~$ sudo ndiswrapper -i /home/maddbaron/Desktop/bcwl5.inf
bcwl5 is already installed. Use -e to remove it


yup its on the desktop along with the sys file

looks like ndiswrapper is installed but i keep getting invalid driver

---

### Post by squibT on 2006-10-27
Uninstall then reinstall your driver...if you get the same message you need to find the correct drivers...key is correct drivers...you can try reinstalling the same drivers again and maybe they will report correctly...

If not...  uninstall ndiswrapper (see below) then follow my post to reinstall from SP Manager....installl all ndis and then wpa_supplicant if you are using it   


           sudo modprobe -r ndiswrapper 

              sudo apt-get --purge remove ndiswrapper-utils 

              sudo rm -r /etc/ndiswrapper/ 

              sudo rm -r /etc/modprobe.d/ndiswrapper

              sudo rm /lib/modules/$(uname -r)/kernel/drivers/net/ndiswrapper/ndiswrapper.kor.ko

---

### Post by DJ Scribblinni on 2006-10-27
First off, if you haven't already, you can't install a driver on top of one with the same name so a ```
sudo ndiswrapper -e bcwl5
```
that will rid of the driver that ndiswrapper is currently using, then try to ```
sudo ndiswrapper -i /home/maddbaron/Desktop/bcwl5.inf
```
If it still turns up invalid, perhaps you have just that.  Try hooking us up with some info of the hardware that you are using.


**squibT beat me...

---

### Post by nyinge on 2006-10-27
What's your card?  I used to get a similar error when some needed files are missing.  Yes, you've got the sys file, but could there be others as well?

---

### Post by squibT on 2006-10-27
> **DJ Scribblinni said:**
> First off, if you haven't already, you can't install a driver on top of one with the same name so a ```
sudo ndiswrapper -e bcwl5
```
that will rid of the driver that ndiswrapper is currently using, then try to ```
sudo ndiswrapper -i /home/maddbaron/Desktop/bcwl5.inf
```
If it still turns up invalid, perhaps you have just that.  Try hooking us up with some info of the hardware that you are using.


**squibT beat me...

Haaa...good point Scribblinn...uninstall first.

Make sure you are in Desktop/bcwl5/

Then exe the inf file: Desktop/bcwl5/bcwl5.inf

---

### Post by maddbaron on 2006-10-27
> 
maddbaron@baronworks:~$ sudo ndiswrapper -e bcwl5
maddbaron@baronworks:~$ sudo ndiswrapper -i /home/maddbaron/Desktop/bcwl5.inf
Installing bcwl5
cp: cannot stat `/home/maddbaron/Desktop/bcwl5.inf': No such file or directory
maddbaron@baronworks:~$ sudo ndiswrapper -l
Installed ndis drivers:
bcwl5   invalid driver!


I'm on an acer aspire 3000 laptop.

The driver worked in dapper, i dont understand this. Its the very same driver.

So remove ndiswrapper?

---

### Post by squibT on 2006-10-27
Yes start fresh...I had the same problems ...so have others...

---

### Post by maddbaron on 2006-10-27
ok I'll remove it...this is so befuddling...the driver is on the Desktop both of them .inf and .sys, those were only two I used in dapper. 

very befuddling...

---

### Post by maddbaron on 2006-10-27
ok, removed all.

---

### Post by squibT on 2006-10-27
You keep posting sudo ndiswrapper -i /home/maddbaron/Desktop/bcwl5.inf

That is not the location of your driver when you first posted. It was in a bcwl5 dir. If it is on the Desktop now uninstall it and reinstall it. You may want to unistall everything and start fresh...

Dont worry...just keep at it...you will get it.

---

### Post by nbound on 2006-10-27
if your talking about the **bcmwl5.inf** driver for broadcom 4318's try the install howto i made here: [http://www.ubuntuforums.org/showthread.php?t=285809](http://www.ubuntuforums.org/showthread.php?t=285809)

(it may work with other broadcom cards too... but cant be sure - the others should run on the native drivers though anyway)

---

### Post by maddbaron on 2006-10-27
whooo hooo it worked!

I uninstalled like you said then used adept to install and I used the gui adept had for ndiswrapper then I just installed it through that and it works! YES!!!!!!!!! my orange light is on....YESSSSSSSS!!!!!!!!!!

thanks folks...

one last question,

Do I need to keep the .inf file on my desktop for it to work?

---

### Post by maddbaron on 2006-10-27
i think i need to reboot. my orange is on but i took out my cable and i lost connection...i added wifi-radar it said i was connected...gonna reboot.

---

### Post by squibT on 2006-10-27
Congrats...no...it should be filed  away for future use.

Later....

---

### Post by mavr on 2006-11-01
i tried reinstalling the whole thing. but my modprobe keep giving me an error. :( My blue light never turns on :(

---

### Post by mavr on 2006-11-05
i had troubles, my ndiswrapper was working properly but i couldn't get my wlan usb light to blink. I followed the advice to reboot without the usb connected and then when i connected it all worked. Try it too people. It seems like ndiwsrapper didn't load properly at boot if the usb was connected.  Thanks to everybody for the help

---

