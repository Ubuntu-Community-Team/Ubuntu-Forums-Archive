---
title: "Ati 4850 Extra effects drivers"
date: 2009-06-26
forum: New to Ubuntu
---

### Post by Grobsy on 2009-06-26
Hello,
today i started using Ubuntu 8.04, and I really like it.
I was looking forward to all the fancy effects from Compiz, but when i try to enable Extra visual effects, i get the error message "Desktop effects could not be enabled".
I use a Ati 4850 graphics card and a AMD x2 6000+ processor.
I heard that there are sometimes problems with drivers on Ubuntu, especially with the 4850.
Can you please help me?
Thanks!

(I probably made a lot of grammar mistakes, English isnt my native language)

---

### Post by porchrat on 2009-06-26
Under System --> Administration --> Hardware Drivers you should find the proprietary ATI drivers for ubuntu. Select them and they should install automatically, restart and compiz should work.

There is also an issue with early versions of the 4850 cards, the firmware was faulty and didn't make the fan on the card run properly allowing the card to heat up to dangerous temperatures, after installing the drivers use the temperature checking feature to make sure your card is OK. [Here]("http://ubuntuforums.org/showthread.php?t=941732") is a HOWTO from a ways back that I wrote that will help you to do this.

---

### Post by Grobsy on 2009-06-26
No proprietary drivers installed.
The list is empty.

---

### Post by porchrat on 2009-06-26
> **Grobsy said:**
> No proprietary drivers installed.
The list is empty.

Alternatively you can download the latest drivers directly from the ATI website [here]("http://ati.amd.com/support/driver.HTML"). Just select the appropriate options and download (it is around 80MB).

The reason I didn't mention this previously is because these drivers are not yet officially stable on Ubuntu (as far as Canonical is concerned) and that they can cause problems.

If compiz is worth it to you then go for it. I use the latest drivers generally without issue, but I have had problems.

You could try updating your repositories and see if the restricted driver shows up then.

Using this command:
```
sudo apt-get update
```

Then check the restricted drivers again and they may have shown up.

---

### Post by Grobsy on 2009-06-27
A stupid question, but,
How do I run the program i Downloaded from the ati site?

---

### Post by 3rdalbum on 2009-06-27
First, run all software updates so you have the latest kernel.

Next, install the "build-essential" and "linux-headers" package from Synaptic Package Manager. These are required for the manual ATI driver install.

Now, open a terminal. On Linux you need to make a program executable before it can be run, so you do this:

```
sudo chmod a+x <drag the file to the terminal and press Enter>
```

The terminal will automatically fill in the filename for you. Make sure there's a space in between "x" and the filename. (There is a graphical way to make a program executable by root, but it takes longer).

Now you need to run the installer. You need to run it as root (administrator) because your normal user account is prohibited from writing to system-wide locations.

```
sudo <drag the file to the terminal>
```

Again, there should be a space in between the "o" and the filename. "sudo" means "run the following as root".

That should do it.

---

### Post by Grobsy on 2009-06-27
Could not open the file /home/gerben/Desktop/ati&#8230;taller-9-6-x86.x86_64.run using the Unicode (UTF-8) character coding.



Got the above error. What to do?
I assume that with getting the latest software upgrades you mean running the update manager? Or do I have to go from 8.04 to the newer ubuntu?


[https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/linux_cat95-inst.pdf](https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/linux_cat95-inst.pdf)

that&#347; the installation manual, but there's a lot of stuff in it that I don't understand. 
Required programs I can't find in the package manager etc.
Could someone please so kind to help me with those?:oops:
I'm kind of new to all the package manger stuff :P


Edit: I tried installing the Xorg Graphics accelarator stuff, but hen it broke and went into low graphics mode etc.

---

### Post by porchrat on 2009-06-28
> **3rdalbum said:**
> First, run all software updates so you have the latest kernel.

Next, install the "build-essential" and "linux-headers" package from Synaptic Package Manager. These are required for the manual ATI driver install.

Now, open a terminal. On Linux you need to make a program executable before it can be run, so you do this:

```
sudo chmod a+x <drag the file to the terminal and press Enter>
```

The terminal will automatically fill in the filename for you. Make sure there's a space in between "x" and the filename. (There is a graphical way to make a program executable by root, but it takes longer).

Now you need to run the installer. You need to run it as root (administrator) because your normal user account is prohibited from writing to system-wide locations.

```
sudo <drag the file to the terminal>
```

Again, there should be a space in between the "o" and the filename. "sudo" means "run the following as root".

That should do it.

The method described above is the best way to do it. The method above will launch a graphical installer program that is far easier to use than doing it through the command line.

When you want to install it first change it's permissions to ensure that your user can execute it (much like a Windows user would execute a .exe file) by using this command (this command assumes that the file is on your users Desktop):
```

chmod u+x /home/username/Desktop/ATI_installer_filename.run
```

Then all you need to do is run it from the command line using sudo:
```

sudo /home/username/Desktop/ATI_installer_filename.run
```

"user" is your username and "ATI_installer_filename.run" is the name of the particular installer file you downloaded.

It will then bring up a graphical installer like you would get in Windows. Choose the options that you would like or just let it do a default install and you should be good to go.

If not pelase report back and let us know what is up.

> **Grobsy said:**
> Could not open the file /home/gerben/Desktop/ati&#8230;taller-9-6-x86.x86_64.run using the Unicode (UTF-8) character coding.



Got the above error. What to do?
I assume that with getting the latest software upgrades you mean running the update manager? Or do I have to go from 8.04 to the newer ubuntu?
No he just means type this command in the command line:
```
sudo apt-get update
```
This command will just make your OS check which are the latest versions of everything on the repositores. Then check your update manager to see if you have any files that need updating. This just ensures that your system is completely up-to-date because otherwise the new drivers can cause trouble.

> 
[https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/linux_cat95-inst.pdf](https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/linux_cat95-inst.pdf)

that&#347; the installation manual, but there's a lot of stuff in it that I don't understand. 
Required programs I can't find in the package manager etc.
Could someone please so kind to help me with those?:oops:
I'm kind of new to all the package manger stuff :P
You shouldn't need to worry about installation manuals. As I mentioned above there is actually a graphical installater program that comes with that driver, it should take care of all the packages that you need to get the driver running.

> 
Edit: I tried installing the Xorg Graphics accelarator stuff, but hen it broke and went into low graphics mode etc.
Please give us the output of this command:
```
fglrxinfo
```

---

### Post by Grobsy on 2009-06-28
Command output:
gerben@gerben-desktop:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org]("http://www.mesa3d.org")
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.4 (2.1 Mesa 7.0.3-rc2)

gerben@gerben-desktop:~$ 



I had to reinstall ubuntu because I didn't know what to do when it was in text-mode etc. so I dont know if this is still any use to you.








When i try to run the command
```
sudo chmod a+x filename
``` etc.
I get this error:

Could not open the file /home/gerben/Desktop/ati&#8230;taller-9-6-x86.x86_64.run.
gedit has not been able to detect the character coding.
Please check that you are not trying to open a binary file.
Select a character coding from the menu and try again.

Character coding: Current locale (UTF-8 )


Also there's a lot 'linux-headers' and 'build essential' packages
which one to take?




Also heard people saying ATI doesn't work too good with Linux. Is this true? Would it be better to switch to 9.04?
Oh and Compiz is worth it to me. I like customizing and the world of window managers etc. is what pulled me to linux in the first place :P

Thanks in advance, no trying to be a help vampire

---

### Post by porchrat on 2009-06-28
> **Grobsy said:**
> Command output:
gerben@gerben-desktop:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org]("http://www.mesa3d.org")
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.4 (2.1 Mesa 7.0.3-rc2)

gerben@gerben-desktop:~$ 

I had to reinstall ubuntu because I didn't know what to do when it was in text-mode etc. so I dont know if this is still any use to you.


Not a problem, it just means that the ATI driver hasn't been installed yet then (we can see that from all the "Mesa" stuff being returned there). For future reference you can sometimes fix the graphics by booting into recovery mode and selecting the "repair X server" (or something like that I forget the exact wording), or by entering "dpkg-reconfigure xserver-xorg" into the command line (which essentially that text mode that you were talking about).

> 
When i try to run the command
```
sudo chmod a+x filename
``` etc.
I get this error:

Could not open the file /home/gerben/Desktop/ati&#8230;taller-9-6-x86.x86_64.run.
gedit has not been able to detect the character coding.
Please check that you are not trying to open a binary file.
Select a character coding from the menu and try again.

Character coding: Current locale (UTF-8 )

OK it looks as though you are trying to use gedit to open that ati&#8230;taller-9-6-x86.x86_64.run file? If so that is not what you should be doing, do not use the word "gedit" in any of the commands. You need to run it as though it were a program in itself, gedit is only used as a text editor to open text files, it cannot be used to execute files. This is the command you need to use to run that .run file:

```
sudo sh /home/user/Desktop/ati&#8230;taller-9-6-x86.x86_64.run
```
OR
```
sudo /home/user/Desktop/ati&#8230;taller-9-6-x86.x86_64.run
```

Again this assumes that that installer .run file is on your Desktop and that your username is "user". Feel free to alter the command to suit your needs. 

> 
Also there's a lot 'linux-headers' and 'build essential' packages
which one to take?


You are going to need the "build-essential" package and the linux-headers package that corresponds to your kernel, as well as a few other packages. These can be attained using this command (I can't remember if you need all of these, but you may as well just get them all):
```
sudo apt-get install build-essential cdbs fakeroot dh-make debhelper debconf libstdc++5 dkms linux-headers-$(uname -r)
```

The "$(uname -r)" part will ensure that you get the linux-headers that correspond to your current kernel, that way you don't need to worry about looking up your kernel and entering that number, it is a useful trick to remember.


> 
Also heard people saying ATI doesn't work too good with Linux. Is this true? Would it be better to switch to 9.04?
Oh and Compiz is worth it to me. I like customizing and the world of window managers etc. is what pulled me to linux in the first place :P


In my opinion ATI works well enough for what I need it for. Compiz, a few small games etc.

Personally, I think 9.04 ROCKS. It is a lot faster than 8.04 and has some fun themes. Although I'm sure you can get these themes of the internet and integrate them into 8.04 if you desired. Also keep in mind that 8.04 is a Long Term Support (LTS) release, meaning that it will be supported by Canonical long after support for 9.04 is over. 9.10 is the next LTS if I remember correctly, 9.04 is also going to be the first version of Ubuntu to run ext4 as a stable standard (43% faster than ext3 in some cases). My advice is to move to 9.10 when it is released (that is what I will be doing), but keep in mind that I live in a country where internet is rather expensive so I can't afford to download every version of Ubuntu. I still run 8.04 and I love it.

Some do say that the ATI installs can be a little trickier, but I have never had any serious problems.

I have to agree that compiz is worth the risk, unless it is a production system of course.

> Thanks in advance, no trying to be a help vampire
Please don't worry about that, everyone needs to learn somehow and most on these forums are here because they want to help new users and because they want to further their own knowledge. I think it is a small way of giving back to the community for everything we have all received from Ubuntu.

If I can in some way help you to resolve your problem then I am happy. :)

---

### Post by Grobsy on 2009-06-29
It works now. Thanks for helping :p

---

### Post by porchrat on 2009-06-29
> **Grobsy said:**
> It works now. Thanks for helping :p

No problem, hope I helped a little. Enjoy compiz :)

---

