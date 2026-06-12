---
title: "Wireless LAN card is not working!"
date: 2009-07-07
forum: New to Ubuntu
---

### Post by Angeline_ on 2009-07-07
When I had intrepid on my laptop (Compac cq50),everything seems worked just fine. I have just installed Ubuntu 8.10  and everything seems to be working fine except for the wireless LAN card(Atheros 802.11 wifi). 

I've tried several method I found in the web but it doesn't solve my problem.:mad:

Did anyone faced the same problem like I do?

---

### Post by poosietgp on 2009-07-07
Hi try installing the linux-backports-modules.

make sure the kernel version of the backports module you are gonna get is a lower number than kernel you are using. :)

---

### Post by nhasian on 2009-07-07
alternatively you can try the newer ubuntu 9.04 as it has more wifi drivers.

---

### Post by Angeline_ on 2009-07-07
okay! do i need to format my pc all over again like how i install 8.10?
Or just urgrade my current ubuntu 8.10?

---

### Post by nothingspecial on 2009-07-07
Copy and paste these lines into your teminal

Download the latest madwifi drivers

```
wget http://snapshots.madwifi-project.org/madwifi-hal-0.10.5.6-current.tar.gz
```

Install some software neccesary for compiling
```
sudo apt-get install build-essential linux-headers-$(uname -r)
```

Extract the drivers
```
tar -xzf madwifi-hal-0.10.5.6-current.tar.gz
```

Get into the drivers directory
```
cd madwifi-hal-0.10.5.6*/
```

Compile
```
make
```
```
sudo make install
```

Load the drivers
```
sudo modprobe ath_pci
```

Make the drivers load everytime you boot
```

gksudo gedit /etc/modules
```

Type this line at the bottom of that file

```
ath_pci
```

save
close
reboot

Do not delete the madwifi directory you hav downloaded. (You can delete the .tar.gz)

Every time you get a new kernel you will have to recompile the drivers. This is very easy.

```
cd madwifi-hal-0.10.5.6*/
``````

make clean
```
```
sudo make install
```
reboot

---

### Post by nothingspecial on 2009-07-07
> **Angeline_ said:**
> okay! do i need to format my pc all over again like how i install 8.10?
Or just urgrade my current ubuntu 8.10?

Which ever way you like. Or you can try the above instructions which worked for me every time on 8.10

---

### Post by Angeline_ on 2009-07-07
> **nothingspecial said:**
> Copy and paste these lines into your teminal

Download the latest madwifi drivers

```
wget http://snapshots.madwifi-project.org/madwifi-hal-0.10.5.6-current.tar.gz
```Install some software neccesary for compiling
```
sudo apt-get install build-essential linux-headers-$(uname -r)
```Extract the drivers
```
tar -xzf madwifi-hal-0.10.5.6-current.tar.gz
```Get into the drivers directory
```
cd madwifi-hal-0.10.5.6*/
```Compile
```
make
``````
sudo make install
```Load the drivers
```
sudo modprobe ath_pci
```Make the drivers load everytime you boot
```

gksudo gedit /etc/modules
```Type this line at the bottom of that file

```
ath_pci
```save
close
reboot

Do not delete the madwifi directory you hav downloaded. (You can delete the .tar.gz)

Every time you get a new kernel you will have to recompile the drivers. This is very easy.

```
cd madwifi-hal-0.10.5.6*/
``````

make clean
``````
sudo make install
```reboot


Thank you for your help! I've tried ur method but this appear when I enter this code:


eangelin@angeline-laptop:~$ cd madwifi-hal-0.10.5.6*/
bash: cd: madwifi-hal-0.10.5.6*/: No such file or directory
angeline@angeline-laptop:~$ make
make: *** No targets specified and no makefile found.  Stop.
angeline@angeline-laptop:~$ sudo make install
make: *** No rule to make target `install'.  Stop.
angeline@angeline-laptop:~$ sudo modprobe ath_pci
WARNING: /etc/modprobe.d/blacklist line 46: ignoring bad line starting with 'sudo'
WARNING: /etc/modprobe.d/blacklist line 47: ignoring bad line starting with 'ndiswrapper'
angeline@angeline-laptop:~$ gksudo gedit /etc/modules

may i know why is is like this?
Did i miss out any command?

---

### Post by Angeline_ on 2009-07-07
Still struggling how to solve my prob!!

---

### Post by random turnip on 2009-07-07
Mine didn't work in 8.10, but i installed 9.04 and it worked instantly, try an upgrade and see if that does the trick.

---

### Post by Ranemills on 2009-07-07
With the "cd madwifi-hal-0.10.5.6*/" command, it requires that the .tar.gz file has been extracted to home. You need to change the directory to where ever the .tar.gz file has been extracted or you could copy it to the home.

---

### Post by Angeline_ on 2009-07-07
> **Ranemills said:**
> With the "cd madwifi-hal-0.10.5.6*/" command, it requires that the .tar.gz file has been extracted to home. You need to change the directory to where ever the .tar.gz file has been extracted or you could copy it to the home.
 
Still don't understand.....:mad:

---

### Post by Angeline_ on 2009-07-07
> **random turnip said:**
> Mine didn't work in 8.10, but i installed 9.04 and it worked instantly, try an upgrade and see if that does the trick.
 
 
Can i just upgrade it without formatting my pc?
Do there any option/choices for upgrade?
Because i get bored formatting it anymore.....:p;)
 
Thanks for your help..

---

### Post by LewRockwell on 2009-07-07
> **Angeline_ said:**
> Still don't understand.....:mad:

Nobody can help you more than YOU can help you

Get 9.04 Jaunty and use the LiveCD test-drive function to see how it will perform on your specific machine

Then, after you've done that you can let us know how that worked out for you

It doesn't get ANY simpler than that

.

---

### Post by Angeline_ on 2009-07-07
> **LewRockwell said:**
> Nobody can help you more than YOU can help you
 
Get 9.04 Jaunty and use the LiveCD test-drive function to see how it will perform on your specific machine
 
Then, after you've done that you can let us know how that worked out for you
 
It doesn't get ANY simpler than that
 
.
 
 
Okay, then i'll try it myself  1st, will ask for your help later..!
Tq.

---

### Post by nothingspecial on 2009-07-07
You did follow my instructions with a wired internet connection?

I should have mentioned it.

---

### Post by Nathan Cunningham on 2009-07-07
I had the same problem. It was a silly mistake on my part. Go to:
System<Administration<Hardware Drivers
There should be available drivers and your LAN card should be there with the appropriate driver. This may have been disabled along the way. Authenticate it with your system password and it should be good to go.

---

