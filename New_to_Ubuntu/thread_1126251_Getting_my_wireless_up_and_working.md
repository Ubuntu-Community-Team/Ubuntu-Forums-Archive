---
title: "Getting my wireless up and working"
date: 2009-04-15
forum: New to Ubuntu
---

### Post by Bensimgym on 2009-04-15
Hi there  - very new to linux and having sorted out a lot a problems since I started installing Ubuntu 8.10 on my Acer Aspire One I am flagging.

I am following the installation documentation at 

[https://help.ubuntu.com/community/AspireOne](https://help.ubuntu.com/community/AspireOne)

I have got as far as You may need to append ath_pci to/etc/modules:

I have not got the faintest idea how to do it or the next one to stop the workeless going to sleep on suspend function.

Please I have got so far (its taken me 5 days)  how do I add these scripts?

Hoping you can help me

Ben

---

### Post by Jakey_TheSnake on 2009-04-15
Please see my HOWTO here: [http://ubuntuforums.org/showthread.php?t=1022698](http://ubuntuforums.org/showthread.php?t=1022698)

I believe you would be after the "modprobe" command at the end :)

Then restart.

edit: if you have done this, then run: ```
sudo gedit /etc/modules
``` 

And add ath_pci on the end like it says.

Then: ```
sudo gedit /etc/pm/sleep.d/00wireless
``` 

Paste into the document this: ```
#
# Restart WiFi interface after suspension
#

case "$1" in
        resume|thaw)
                /sbin/ifconfig wifi0 down
                /sbin/ifconfig wifi0 up
        ;;
        *)
        ;;
esac

exit $?
```

Then run: ```
sudo chmod u+x /etc/pm/sleep.d/00wireless
```

And I wouldn't do the LED lights one, it gets really annoying and isn't worth it.

---

### Post by iponeverything on 2009-04-15
Hi Ben -- hang in there.

open a terminal and 
append the ath_pci to /etc/modules like so:

```
sudo echo ath_pci >> /etc/modules

```

in a terminal --
to stop on it on suspend:

type

```
sudo cat >> /etc/pm/sleep.d/00wireless
```

copy the following code segment:

```

#
# Restart WiFi interface after suspension
#

case "$1" in
        resume|thaw)
                /sbin/ifconfig wifi0 down
                /sbin/ifconfig wifi0 up
        ;;
        *)
        ;;
esac

exit $?

```

and paste it into the terminal.  

Then type "ctrl+D"

then do:
```
sudo chmod u+x /etc/pm/sleep.d/00wireless

```

---

### Post by arochester on 2009-04-15
Notice that the instruction > You may need to append ath_pci to/etc/modules: has a colon on the endThe bit is the box that follows is the ath_pci bit. What it means is you may need to add the ath_pci bit to /etc/modules. Open /etc/modules with this command > gksudo gedit /etc/modules. Copy and paste the ath_pci bit. Save. Exit.

---

### Post by Bensimgym on 2009-04-16
Hi there again

When I try to do anything I get permission denied returned in turminal - I take it this might be because I am not in at roote level???????

Ben

---

### Post by nothingspecial on 2009-04-16
Did you use gksudo then type your password?

Copy and paste this into your terminal.

```
gksudo gedit /etc/modules
```

then type your password.

You will see a file that looks like this

```
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

fuse
lp
```

You want it to look like this
```

# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

fuse
lp
ath_pci
```

Save it 
Close 
Reboot

---

### Post by Jakey_TheSnake on 2009-04-16
If you copied and pasted my commands exactly from the code box, and then entered your password you would not be getting "access denied". 

Please note that the password prompt is blank, and you will not see what you are typing, but rest assured it _is_ actually typing.

---

### Post by Bensimgym on 2009-04-16
Hi there  - thanks for all your help and I have been able to run the changes and script - however, - even when I reboot I cannot get wireless connection.

I had it oriiginally 2 days ago - the connection is listed on connection but I cannot connect - any suggestions - I am turning to hysterical laghter now - if i don't laugh then I would cry - I am learning a lot but I want to use my netbook on wireless

Regard  Ben

---

### Post by nothingspecial on 2009-04-16
There has been a recent kernel update.

This means that the madwifi drivers you installed earlier wont work anymore because they are attached to the previous kernel.

If you still have the madwifi directrory the cd into it. If it`s in your home directory then

```
cd madwifi-hal-0.10.5.6*/
```

Then ```
make clean
```

```
sudo make install
```

If you`ve deleted it you`re going to have to the whole thing again. Unless it`s still in your trash.

---

### Post by Bensimgym on 2009-04-16
Thank you thank you thank you

I am now on wireless!

Sincere thanks for all of your help - you never know I might become an expert - eventually!!!!

Ben

---

### Post by nothingspecial on 2009-04-16
Cool  :guitar:

---

