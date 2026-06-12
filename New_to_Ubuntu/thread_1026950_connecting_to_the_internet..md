---
title: "connecting to the internet."
date: 2008-12-31
forum: New to Ubuntu
---

### Post by blueloom on 2008-12-31
I know this question has been answered a million times already, but I'm a newbie.  I have installed ubunta 8.01 that was with the book,  "Ubunta for non-geeks".  It is the hardy heron edition.  

It loaded fine, works fine, but I have dial up and it couldn't find the modem.  I purchased a used  usr courier V everything modem and have it hooked up to my external serial port.  Nothing.  I have tried a few different dos settings to no avail.

I know the modem works as I have used it on another computer with windows.  I tried to download the scan modem program, but it won't download on windows and of course linux won't go on the internet. There seem to be some other downloads that could maybe help me, but again, I can't download in linux.

I have usb ports and even tried an adapter from serial to usb 2 hoping it could find the modem.  From what research I have done on the linux sites, this modem should work and it seems that everyone recomends an external modem for linux.

I am at a dead end.                blueloom:

---

### Post by Tim Sharitt on 2008-12-31
There is a manual to the modem at [http://www.aces.edu/department/ctu/general/courier.txt](http://www.aces.edu/department/ctu/general/courier.txt) 
There is another one at [http://www.usrobotics.com/support/s-cour/s-cour-docs/1024492.pdf](http://www.usrobotics.com/support/s-cour/s-cour-docs/1024492.pdf) but the only thing relevant for linux was to turn DIP switch 3 off and turn 4 and 8 on

---

### Post by blueloom on 2008-12-31
Thank you Tim.  I'll take a look at those and try the dip switch settings.                blueloom

---

### Post by blueloom on 2008-12-31
Hi Tim.   No luck at all with changing dip switches.  Not one peep from the modem, no blinking lights, nothing.  I looked over the manuals, but could see nothing more to do.   blueloom

---

### Post by _duncan_ on 2009-01-01
1. It might be useful if you provide details on what you're doing to make the external serial hardware modem work. Simply saying a modem doesn't work is vague. It helps to show stuff like configuration files, error messages, etc.

2. It is possible to use a hardware modem even if it is not automatically detected by the system, as long as you know which port to point to in your dialer program. Modems connected via serial ports are usually /dev/ttyS0 or /dev/ttyS1.

3. [_[COLOR="Blue"]This[/COLOR]_]("https://wiki.ubuntu.com/DialupModemHowto") wiki contains a wealth of info on how to connect using dial-up. It's a bit dated, but is still valid AFAIK.

---

### Post by blueloom on 2009-01-01
Hi Tim.    Thank you for the references.  I looked through a lot of them and decided I needed some more linux tools to help me out.  I had another cd version here (Gnome) that included wvdial and gnome ppp, so I loaded the cd version to see what I could find out.

      I got a little farther and did get the lights on the modem to blink, but no results yet.  I got the following report:

    wvdial  internet dialer version 1.54.0
    > initializing modem
    > sending atx3
    0
    >sending ATQ0
    0
    >sending atx3
    0
     >  modem not responding

     Also when I'm going through the process of setting up the network interface it tells me I need kd netwrok-kppp-provider package, and of course it tries to download it.  The program does allow me to continue.

     I have the modem hooked up with a serial cable and everything worked fine on my other computer (microsoft).  I did look up the modem numbers and supposedly it works with linux.  I do think linux is now trying to communicate with my modem.  Any ideas?           blueloom

---

### Post by _duncan_ on 2009-01-02
Not sure if you are talking to Tim or me, but I'll butt in anyway. :)

1. Which Kubuntu version were you referring to in the 1st post, Kubuntu 8.10 or Kubuntu 8.04? There is no version 8.01. This is important coz my understanding is KPPP comes with the default 8.04 but was dropped from 8,10.

2. I'm confident your serial hardware modem will work with linux. It is just a matter of configuring a dialer program correctly. (wvdial, pppconfig, gnome-ppp or kppp).

3. From your last post, I'm assuming you are running off the live CD? Can you give me the exact version?

--------------

For troubleshooting purposes, it is best to focus on an installed version rather than liveCD. The trouble with using live CD is when you power off, all the config files will be lost, so it's difficult to back-track. It's also better to focus on using one dialer program at a time.

---

### Post by blueloom on 2009-01-02
Hi and thanks so much for replying.  I installed ubunta onto my computer and it is Ubunta desktop cd 8.04.   It didn't have the wvdialer or ppp.  I didn't get anywhere with it.  After reading some of the info I was referred to, I decided to use a cd copy of gnome that I had.   I didn't install it, just ran it from the cd and that seemed to work better as it had the two auxillary programs. 

My wife thinks I am crazy to go through all this when for a few bucks I could buy a new computer, but I really like the idea of linux and love the flexibility and the wealth of browsers and programs available.  

My modem is a us robotics courier V everything.  It is supposed to be 56 K and it does work on other programs.  I've tried different dip switch settings.            keith

---

### Post by blueloom on 2009-01-02
Hi Duncan.   I just booted up ubuntu and checked the programs I have loaded on it.  I don't have the kppp dialer tool.  My problem is that I don't think I can download it on my microsoft program.  Am I right in that assumption????   Also, how do I decide if it is safe to download something???   

        My problem is I need internete access to solve my problem and I can't get on the internet, just enough to pester you guys.                 keith

---

### Post by sadaruwan12 on 2009-01-02
> **blueloom said:**
> Hi Duncan.   I just booted up ubuntu and checked the programs I have loaded on it.  I don't have the kppp dialer tool.  My problem is that I don't think I can download it on my microsoft program.  Am I right in that assumption????   Also, how do I decide if it is safe to download something???   

        My problem is I need internete access to solve my problem and I can't get on the internet, just enough to pester you guys.                 keith
Hi,

blueloom I think it's better to go with an ADSL router/modem 'cos configuring a modem is some times very hazerdes it's very easy to work with a router on a Ubuntu or Linux system.

---

### Post by _duncan_ on 2009-01-02
Let's take this one step at a time, shall we?

Right now, I'm still trying to figure out what you really installed in your computer. The thread title says "[kubuntu]...", meaning Kubuntu 8.04. This is different from Ubuntu 8.04.

If you don't know the difference, Kubuntu will give you a default bluish desktop theme. Ubuntu color theme is brown/orange. It is important to settle this first coz they have different default packages installed.

---

### Post by blueloom on 2009-01-02
I'm going to plead ignorance.  I don't know what an adsl router is.  I only have dial up phone service and have tried, but can't get dsl service here.   Does an adsl router/modem work on just a phone line or does it need dsl?   Thanks,   keith

---

### Post by blueloom on 2009-01-02
Hi.  I'm sorry.  I have ubuntu.  These terms are new to me.  It is ubuntu 8.04 and I got the cd with the book Ubunta for non geeks,  3'rd edition.  I am definitely a non-geek.    keith:popcorn:

---

### Post by _duncan_ on 2009-01-03
OK, Ubuntu 8.04 it is then.

1. There are no graphical dialer programs installed by default with this version. However, there are 2 terminal (text) based dialers installed: **wvdial** and **pppconfig**. Note, you don't have to download anything to use these 2.

2. Let's try using **wvdial**:

2.a  Boot up Ubuntu, make sure your serial modem is connected and turned on.

2.b  Open up a terminal by clicking Applications > Accessories > Terminal.

2.c  Enter the following into the terminal.```
sudo wvdialconf
```
You will be prompted for your password, then wvdial will attempt to detect your modem.

2.d  If successful, wvdial will create a basic configuration file _/etc/wvdial.conf_. On the same terminal, type in the following:```
sudo gedit /etc/wvdial.conf
```

2.e  A text editor window will pop up. The contents should resemble the following:```
[Dialer Defaults]
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Modem Type = Analog Modem
; Phone = <Target Phone Number>
ISDN = 0
; Username = <Your Login Name>
Init1 = ATZ
; Password = <Your Password>
Modem = /dev/ttyS0
Baud = 460800
```

2.f  Those lines starting with a semicolon is where you enter your ISP login information. Also, remember to remove the semicolon character such that the file looks like this:```
[Dialer Defaults]
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Modem Type = Analog Modem
Phone = 1234567
ISDN = 0
Username = loginName
Init1 = ATZ
Password = loginPassword
Modem = /dev/ttyS0
Baud = 460800
```

2.g  Note You have to replace 1234567, loginName and loginPassword with your own data.

2.h  Save the file and exit.

2.i  To try connecting to your ISP, enter the following into the terminal:```
sudo wvdial
```

---

### Post by blueloom on 2009-01-03
Hi.  I get the message "unable to resolve host sbcglobal" which I assume means I am not getting logged on.  I sign in with name and password initially, but didn't get the prompt for password when I opened terminal.  I usually get the prompt when I go into other applications, but didn't get it for terminal.

when I open terminal, I get the message:

      keith@sbcglobal:~$    and a blinking cursor following that.  I just typed in the message you suggested and hit return.  

                                     keith

---

### Post by _duncan_ on 2009-01-03
> I get the message "unable to resolve host sbcglobal" which I assume means I am not getting logged on

Enter this command on the terminal:```
sudo touch /etc/resolv.conf
```

then try dialing in again.```
sudo wvdial
```

Seems like your logging in successfully to your ISP, but the DNS server is not being set dynamically. It's a known problem with wvdial.

----------------------

Not sure I understand the rest of your message about password.

---

### Post by blueloom on 2009-01-03
Hi Duncan.  I think I'm jinxed.   I'm going to type in the command exactly the way I did after I got your message.  

    sudo touch/etc/resolv.conf       I got the same message.  Unable to resolve host sbcglobal.  

    The password I mentioned because you said I should get a password prompt when I opened terminal.  Didn't get one.

    Thank you for all your patience.  I'm wondering if I should order another cd.  It just takes me too long to download.

                                             keith  :confused:

---

### Post by _duncan_ on 2009-01-03
Where are you gettting the error message? Terminal? Firefox?

If it's firefox, make sure it is not set to work offline. Click <File>, then look for the entry "Work Offline" at the bottom part of the menu.

---

### Post by blueloom on 2009-01-03
I'm getting the message in terminal.     keith

---

### Post by _duncan_ on 2009-01-03
Can you post the complete sequence of texts displayed by wvdial after entering the command "sudo wvdial"?

---

### Post by blueloom on 2009-01-04
Hi Duncan.

     I get the same message each time.  I can't copy and paste, but I'll type it in below:

   I put in    keith@sbcglobal:~$   sudo wvdial
   I get this   sudo:unable to resolve host sbcglobal

    I've tried putting in    sudo touch/etc/resolv.conf
    I've tried putting in    sudo wvdialconf

  I always get the same message.        keith

---

### Post by _duncan_ on 2009-01-04
I have no idea what's causing it, but it seems tied up to the 'sudo' command, which has nothing to do with dial-up. My hunch is the system was probably borked previously.

If it were my computer, I'd probably reinstall. But there's no guarantee it will solve the problem.

---

### Post by Temposs on 2009-01-04
Support for dialup internet access in ubuntu is really quite horrid. I had to set up my Mom with dialup internet on a new Dell computer pre-installed with Ubuntu, and it was still a major headache(we had to do it over the phone). Wireless internet connections and other high speed connections are SOOOOO easy compared to dialup. They don't require any setup most of the time. They just work!

Oh, and in case you didn't know, a couple companies sell computers preinstalled with Ubuntu, which is quite nice. [Dell]("http://www.dell.com/content/topics/segtopic.aspx/linux_3x?c=us&cs=19&l=en&s=dhs") and [System76]("http://www.system76.com/") build systems with Ubuntu preinstalled

The only program I found to work was pppconfig. No other program wanted to work for me. Since you haven't tried that yet, why don't you give it a shot?

You should search on [this page]("https://help.ubuntu.com/community/DialupModemHowto/SetUpDialer#head-0769b0061bf81bfba710118540bd86223e815761") for "Alternative Way 2 (using pppconfig & pon/poff)". Then, just follow the instructions on there. You should be using pppconfig and pon and poff.

If you can get pon to connect you to the internet(it takes about a minute with the dialing and all that), then you can create a launcher so you have an easy button to connect you to the internet. To do that, right click an empty spot in the top panel, and click "Add to Panel". The first option is "Custom Application Launcher", so click that. For name call it something like "Connect to the Internet". For command, type: "pon"(without quotes, of course). Comment can be anything. Click on the springy icon and a window with a bunch of icons will appear. Choose the one that looks like a telephone :-) Then click ok a couple times and you should have a button on your panel. When you want to dial to the internet, you would just click the button and wait about a minute, then you should be connected. :-) You can move it where you want by right clicking and clicking move.

Hope this is helpful!

---

### Post by blueloom on 2009-01-04
Thanks temposs and thanks Duncan.   I'll check our those places tomorrow.  At least I'm glad that someone else had some problems with dial up.  I was beginning to think I was the lone ranger.

 I don't know how many people there are out there with dial up, but I just can't get regular dsl here and can't afford the dish outfits for just the computer.  

If I ever get on the internet with linux, I'm going to throw a party.                 keith

---

### Post by blueloom on 2009-01-04
One more question and I'm done.  Is there someway for me to download the programs I need with windows.  I can't get on the internet with linux.         Thanks again,    keith

---

### Post by handydan918 on 2009-01-04
> **blueloom said:**
> One more question and I'm done.  Is there someway for me to download the programs I need with windows.  I can't get on the internet with linux.         Thanks again,    keith

Try [this site.]("http://www.getdeb.net/")

You can download the packages you want, and stick them on a flashdrive, or whatever. Then on your kubuntu machine, install them with kpackage.

---

### Post by Temposs on 2009-01-04
hi keith,

If there is a particular program that you want to download, you can try downloading a .deb package file from the homepage of the particular program. .deb files are very easy to install with Ubuntu's default interface. If you can't find that, see below.

You said you're using Ubuntu 8.04, so here's ubuntu's site for package searching, organized by category: [http://packages.ubuntu.com/hardy/](http://packages.ubuntu.com/hardy/)

Here's a link that shows the list of every package succinctly:
[http://packages.ubuntu.com/hardy/allpackages](http://packages.ubuntu.com/hardy/allpackages)

When you click on a particular package to download, go down to the Download section, and click on i386(I assume you have a standard 32-bit processor), then choose some site to download the file from. That should give you a .deb of that package.

Something to watch out for when downloading these programs manually is that programs often depend on other programs, and you need to have every dependency installed before the program you want will be installed. In the "Other packages related to" section of the Ubuntu packages site's page for a particular package, it tells which other packages you need in order to install that particular package. Sometimes they'll already be installed, but sometimes they won't be, and you'll need those as well. But, when you get a connection to the internet, Ubuntu's package manager will automatically figure out which packages you need to install the program you want.

Also, in addition to saying "thanks" for the comments you like, you can also click the icon of a gold medal next to comments that you want to say "Thanks" to :-)

EDIT: Ah yes, you will want to use handydan's recommendation rather than packages.ubuntu.com, as it is more user friendly. But, my warning about dependencies still applies.

---

### Post by _duncan_ on 2009-01-05
Sooner or later, you still have to resolve the problem with the 'sudo' command. Even if you are successful downloading packages via Windows, you won't be able to install these without 'super user' privileges, which the 'sudo' command does.

---

### Post by blueloom on 2009-01-05
Thanks Duncan.   I'll look into the sudo comand and why I can't seem to use it.  What does sudo stand for anyway??

 I actually had to do some work today, so didn't get to "play" with linux today.                  keith

---

