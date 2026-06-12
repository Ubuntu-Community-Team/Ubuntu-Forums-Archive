---
title: "Does a Kodak ESP3 printer work in Lucid?"
date: 2010-06-11
forum: New to Ubuntu
---

### Post by bwallum on 2010-06-11
Hi

I have a Kodak ESP3 all-in-one printer. No trace of it on [www.openprinting.org/printers](www.openprinting.org/printers). Does it work in Lucid please?

Thanks
Bob

---

### Post by halitech on 2010-06-11
there is info here:

[http://sourceforge.net/projects/cupsdriverkodak/](http://sourceforge.net/projects/cupsdriverkodak/)

---

### Post by bwallum on 2010-06-13
Thanks halitech, sorted! I'll paraphrase the process below for anybody following.

How to install a printer driver for a Kodak ESP3 AiO:-

Go to [http://sourceforge.net/projects/cupsdriverkodak/files/]("http://sourceforge.net/projects/cupsdriverkodak/files/")

32bit
-----
If you run 32bit take the easy route and download the c2esp08-1_i386.deb file (or latest) to Desktop, click on the file and install. Switch on printer and go to System>Administration>Printing to check all is in place.

64bit
-----
If you run 64bit then you need to make the driver. Very easy, just more steps.

Download the latest compressed tar file to Desktop. At time of writing this is c2esp08.tar.gz

Extract to Desktop and a folder will appear called c2esp08.

Before we make the file we need some other files to support the make. Open a terminal and```
sudo apt-get install libcups2-dev build-essential cups
```CUPS should be installed already by default. 

Navigate prompt to the folder:-```
cd Desktop/c2esp08
```Your prompt should look like this> ~/Desktop/c2esp08$Now make your driver, first test the file set```
make
```If error free then make the driver and install```
sudo make install
```Switch on printer and go to System>Administration>Printing to check all is in place.

MORE INFORMATION?

Look at the INSTALL file in the downloaded folder.

---

### Post by Jim_in_Omaha on 2010-06-19
> **halitech said:**
> there is info here:

[http://sourceforge.net/projects/cupsdriverkodak/](http://sourceforge.net/projects/cupsdriverkodak/)


It works for my Kodak 5500 Aio with 64 bit.

---

### Post by bwallum on 2010-06-20
Works for me too! Thanks guys!

---

### Post by adam2348 on 2010-07-03
omg thanks to the person who made the driver and you for showing easy steps on how to build it for 64 bit!  it works great for 5100!

---

### Post by pearlie on 2010-08-16
Outstanding! Works for 64bit Lucid, ESP5250

Thanks very much - I've had this printer sitting in the box for 6 months, waiting for a driver to come available. :)

---

### Post by ronparent on 2010-09-30
Wow, truly outstanding. Used the c2esp12 and installed for use with Kodak aio 5300 in Maverick RC.

I've had to switch to windows to use this printer for more than three years! Thank you, thank you, thank you!!!

---

### Post by Yooper on 2010-12-02
Thank you so much for the help.  As you can see I am a very new user with Ubuntu.  This process really just makes my decision to ditch Windows all the better.  THANK YOU.

---

### Post by Spyderkid on 2011-03-25
64bit does not work :(

---

### Post by bwallum on 2011-04-04
> **Spyderkid said:**
> 64bit does not work :(
Can you elaborate a bit more please. Did you follow#3? Where did it go wrong for you? What system are you using?

EDIT
Latest file versions are:-
32bit - c2esp_18-1_i386.deb
64bit - c2esp_18.tar.gz

Both are available at [http://sourceforge.net/projects/cupsdriverkodak/files/](http://sourceforge.net/projects/cupsdriverkodak/files/)

---

### Post by catilley1092 on 2011-07-31
Many, many thanks for this one! Fortunately, I have the 32 bit version of Ubuntu 11.04 (the latest) installed, and this driver worked right off the bat. Without a bunch of commands and sudo to work with.

My printer is the Kodak ESP 3250, so it apparently works with most of the Kodak ESP AIO's. This was the one thing that has held me from a total conversion to Ubuntu/Mint, printing. Many links led to info that Kodak doesn't work with Linux. Whether it 100% works or not, I don't know, but at least now I know that I can print.

NO MORE expensive M$ upgrades for me!:grin:

Now I'll go & see if it works with Mint 11!

Cat

---

