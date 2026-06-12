---
title: "Setting up Dial-up connection on Ubuntu 9.04"
date: 2009-08-22
forum: New to Ubuntu
---

### Post by salil_k on 2009-08-22
Hi,

I am very new to Ubuntu. I recently installed Ubuntu 9.04 and I am trying to set up a dial-up modem connection. I was trying to follow the guides on this forum and on ubuntu's website, [https://help.ubuntu.com/9.04/internet/C/modem-connect.html](https://help.ubuntu.com/9.04/internet/C/modem-connect.html) 

I have acquired scanModem and ran as suggested. For the next step I am trying to find

***System &#8594; Administration &#8594; Network***

but I do not see the Network option under Administration. Can anyone please help me to find this option. I tried finding it evrywhere but dont see it.

As this wasnt working, I tried to set up dial-up connection using Gnome-PPP. 

I could not find Gnome-ppp also so I tried doing:
[B][FONT=Courier New]
sudo apt-get gnome-ppp[/FONT][/B]

but it fails, giving me the error:

[FONT=Courier New]Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Couldnt find package gnome-ppp[/FONT]

So I am kind of stuck. I would really like to get Internet working on ubuntu, and dial-up is my only option. Can anyone please suggest ways to solve the problem? I would much appreciate all the help.

Cheers,
Salil

---

### Post by Bartender on 2009-08-22
salil, I'm a little confused.

Were you connected to the internet when you typed "sudo apt-get gnome-ppp"?

People skip that part of the instructions very often, but you have to be online for a command like that to work.  And you're not online yet with the Linux PC, correct?

Some of us poor dial-up users have been talking about dial-up lately.  If you do a search for 'wvdial' you'll see some of the threads.

You're getting online somehow, apparently.  I'll assume with a Windows PC.  On your Windows PC, do a google search for "ubuntu packages".  I don't know if this is the same website all over the world, but here's the link in the US of A.
[http://packages.ubuntu.com/](http://packages.ubuntu.com/)

Do you have a thumb drive?  Plug it into your Windows PC.  Find the "ubuntu packages" website.  See that line partway down the first page where it says "Search package directories"?  Type in gnome-ppp.  Make sure the "Distribution" line underneath is set to "jaunty".  Ask it to Search.
You should get one result.  Now, a lot of times this doesn't work because of dependencies, but the last time I tried this the "gnome-ppp" package did work as its own separate download.
Download the "gnome-ppp" package to the thumb drive.
In Windows, click on "Remove USB device", then pull out the thumb drive, fire up Ubuntu, plug in the thumb drive, wait for it to be identified on the desktop, and copy the gnome-ppp package to the desktop.  Then double-click on it.

Ubuntu will install the gnome-ppp package.  That gives you the gnome-ppp front end, and it also enables you to set up wvdial manually.

Do a search on the Ubuntu forums for "pppconfig" threads.  Setting up pppconfig is a little confusing at first, but it's the most robust dialer that I know of.  It's fast and as glitch-free as any dialer program in Linux.  Once pppconfig is set up, you open a terminal and type ```
pon
```
to get online, then 
```
poff
```
to get offline.

Once you have pppconfig set up, the gnome-ppp front-end is pretty easy.  By "front-end", I mean that gnome-ppp is just a graphical interface for one of the dialers.  wvdial, I think.   

Having said all that, most winmodems, the kind that come with PC's from the factory, don't work very well with Linux.  Even if you configure pppconfig correctly, that pesky internal modem is likely to give you grief.

---

### Post by lkraemer on 2009-08-22
First open a Terminal and type:
```

sudo wvdialconf /etc/wvdial.conf

```
to see if wvdial is installed.  If not you will need to download it.
If it was installed, it will try to locate and setup the modem and
create the information in /etc/wvdial.conf.

Since you don't have a dialup internet connection you need to
start by going somewhere that has access, borrow their computer, go to
[www.linmodems.org](www.linmodems.org), and download their script to assist in
locating the Winmodem and finding the correct driver.  Save the
script on a USB Flash Drive.

Then download [http://keryxproject.org/download/](http://keryxproject.org/download/) and use it where
you have internet access to get:
Gnome-ppp
wvdial
keryx
(and anything else you want before you get dialup working).

Take those files to your computer on the USB Flash Drive.


Then follow this guide:
[http://ubuntuforums.org/showthread.php?t=1100310&highlight=sm56](http://ubuntuforums.org/showthread.php?t=1100310&highlight=sm56)
Post #4.

Should take 30-40 minutes to be up and running, if your Winmodem 
is supported, or 3-6 days if you must keep bugging the linmodem.org
folks for help and more support.  And your Winmodem might never
be supported or you might never get it working.......maybe!
You can always use an External US Robotics Serial Hardware Modem.

lkraemer

---

### Post by salil_k on 2009-09-04
Hello Bartender,

Thanks for your response. 

I tried doing what you recommended. I downloaded the 'gnome-ppp' package, made sure it was for jaunty. when i opened it on ubuntu (using a pen drive), it opened 'Package Installer' but gave me an error "Error: Dependency is not satisfiable: wvdial" and therefore I could not install the package. I am attaching a screenshot. 

[ATTACH]127373[/ATTACH]

Would you please suggest how to get around this problem? Your help would be really appreciated!

Cheers.

---

### Post by longtom on 2009-09-04
> **salil_k said:**
> Hello Bartender,

Thanks for your response. 

I tried doing what you recommended. I downloaded the 'gnome-ppp' package, made sure it was for jaunty. when i opened it on ubuntu (using a pen drive), it opened 'Package Installer' but gave me an error "Error: Dependency is not satisfiable: wvdial" and therefore I could not install the package. I am attaching a screenshot. 

[ATTACH]127373[/ATTACH]

Would you please suggest how to get around this problem? Your help would be really appreciated!

Cheers.

Just read lkramers post closely.  You will see that he suggest to install wvdial (which is the dependency you need) and go from there.

I have to warn you.  Dial-up in Ubuntu is not for sissies (as they say here) and you will have a bit of patience and be prepared to go the extra mile.  
Jaunty made it even more difficult by not including some essential programs.

That said, there are some excellent folks in this online community who will get you going.  Just stick with it, read carefully and they'll get you up and running.

I had a similar problem [ here ](http://ubuntuforums.org/showthread.php?t=1100310).

Maybe scan through that one and pick out what you can use.

Good luck!:)

---

### Post by salil_k on 2009-09-04
Hi Longtom,

I tried the same with wvdial. I got the package for the website (for jaunty) and tried to install it on ubuntu. it still gave me the same error Error: Dependency is not satisfiable
and therefore, didnt install. :( 

I have also tried to configure dial-up using pppconfig. By following the on-screen instructions, it seems that the configuration happens correctly but when I type in pon in the terminal to connect, nothing happens. typing poff says that there is nothing to be turned off.

---

### Post by longtom on 2009-09-04
> **salil_k said:**
> Hi Longtom,

I tried the same with wvdial. I got the package for the website (for jaunty) and tried to install it on ubuntu. it still gave me the same error Error: Dependency is not satisfiable
and therefore, didnt install. :( 

I have also tried to configure dial-up using pppconfig. By following the on-screen instructions, it seems that the configuration happens correctly but when I type in pon in the terminal to connect, nothing happens. typing poff says that there is nothing to be turned off.

Did you manage to install wvdial?

---

### Post by salil_k on 2009-09-04
Hey longtom,

No, as mentioned before, installing wvdial failed. I obtained the package from ubuntu's packages website but it gave me a "dependency not satisifiable" error and thus, didnt install. I made sure that i obtained the package for the same version of ubuntu that I am using; jaunty.

Cheers.

---

### Post by longtom on 2009-09-04
> **salil_k said:**
> Hey longtom,

No, as mentioned before, installing wvdial failed. I obtained the package from ubuntu's packages website but it gave me a "dependency not satisifiable" error and thus, didnt install. I made sure that i obtained the package for the same version of ubuntu that I am using; jaunty.

Cheers.

I guess you got it from here:

[http://packages.ubuntu.com/jaunty/wvdial](http://packages.ubuntu.com/jaunty/wvdial)

You see the files wvdial depends on (The ones with the red dot).  Make sure they are installed on your PC.

---

### Post by EXCiD3 on 2009-09-04
Like lkraemer mentioned, download [Keryx]("http://keryxproject.org") and then have it download the dependencies for you. Makes life a whole lot simpler for downloading dependencies. :D

---

### Post by Bartender on 2009-09-04
Yeah, sorry for the bad advice - I've read a few posts since that indicated the gnome-ppp package does NOT include some of the necessary dependencies.  I was going to say that you can expand the gnome-ppp package and manually download all the dependencies listed, but those dependencies have dependencies.  I believe this is what was called "dependency hell" back in the days before package managers.

Can you give some more details about pppconfig?  Maybe take a screenshot or write down the details from the summary of the settings for the account you built?  I don't want to disappoint you, but if we can't get pppconfig to dial out, wvdial probly isn't going to work either.  Where this gets seriously messy is if you're trying to get a stupid winmodem to work AND guessing at the proper commands in the dialer.  A new Linux user can waste lots of time trying to figure out the dialer, and it's all for naught if the danged modem isn't going to work. To me, there's no point in trying to learn the pppconfig dialer until you KNOW the modem is ready to go.

When you were setting up pppconfig, what modem was attached and did pppconfig recognize it?

Gawd, dial-up is such a pain!

hi, excid, we talked about Keryx several months back, when you helped me get it up and running with the GUI and all.  At that time you indicated the next version of Keryx should solve the problems I had.  Are we there yet?:)

EDIT: Wanted to mention a command I picked up from forums the other day.  If you're not sure whether something is installed, try this:
which (*program)*

Dangit, the "code" icon isn't available when editing a post.  You have to know the name that Ubuntu uses for the program of course, but I just checked it out on my lappy.  If you just get the bash prompt, the program is not installed.  If you get a response like "/usr/sbin/pppconfig" the program is installed.  Here are my results:

which pppconfig  =  /usr/sbin/pppconfig
which wvdial  = /usr/bin/wvdial
which gnome-ppp  =  /usr/bin/gnome-ppp

---

### Post by LewRockwell on 2009-09-04
> **Bartender said:**
> EDIT: Wanted to mention a command I picked up from forums the other day.  If you're not sure whether something is installed, try this:```
which (*program)*
```Dangit, the "code" icon isn't available when editing a post.  You have to know the name that Ubuntu uses for the program of course, but I just checked it out on my lappy.  If you just get the bash prompt, the program is not installed.  If you get a response like "/usr/sbin/pppconfig" the program is installed.  Here are my results:

```
which pppconfig  =  /usr/sbin/pppconfig
which wvdial  = /usr/bin/wvdial
which gnome-ppp  =  /usr/bin/gnome-ppp
```

why do you need a "code" icon/button?

doesn't [code] work for you?

.

---

### Post by pj_kare on 2009-09-04
Don't know if it will help, but we had the same problem. This is what we did ...
[http://ubuntuforums.org/showthread.php?t=1254368&highlight=wvdial](http://ubuntuforums.org/showthread.php?t=1254368&highlight=wvdial)


Hope it helps ... good luck

---

### Post by EXCiD3 on 2009-09-05
> **Bartender said:**
> hi, excid, we talked about Keryx several months back, when you helped me get it up and running with the GUI and all.  At that time you indicated the next version of Keryx should solve the problems I had.  Are we there yet?:)

We have updated several things, such as downloading recommends and pre-depends so it should be quite on track now compared to when you used it.

For Keryx 1.0 we have picked up using a library that takes care of most of the backend stuff for us and so we can focus on the interface making it simple to use. I'm back at school with a new job and am going to be swamped. If anyone is interested in contributing a little python code to the project, let me know! :D

---

