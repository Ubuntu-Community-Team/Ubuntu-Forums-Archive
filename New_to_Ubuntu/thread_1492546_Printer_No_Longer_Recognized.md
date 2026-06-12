---
title: "Printer No Longer Recognized"
date: 2010-05-24
forum: New to Ubuntu
---

### Post by marenum on 2010-05-24
I left town for the weekend with everything running fine, and when I got back my printer was no longer recognized by the computer. I'm totally clueless, I didn't change a thing. I am running 10.04. Any ideas?

---

### Post by anarchywolf46 on 2010-05-24
What is the computer model and printer model?

I have been hearing about random hardware just not functioning for no reason on 10.04 LTS.

---

### Post by marenum on 2010-05-25
The computer is all custom, the printer is an HP Deskjet F4280.

---

### Post by anarchywolf46 on 2010-05-26
Try one of the ls commands to see if it is recognized. I think that is connected to usb so try lsusb and see if it shows up. Also, check out [https://answers.launchpad.net/ubuntu/+question/4098](https://answers.launchpad.net/ubuntu/+question/4098) and see if maybe something there helps. Other than that, I have no ideas. Sorry. :(

---

### Post by vacc73 on 2010-05-26
[SIZE="5"]***Do you have the HP toolkit installed? If not go into Ubuntu Software center and install it. HP is pretty good usually for suppporting linux, thats why I use their printers:guitar::guitar:***[/SIZE]

---

### Post by finlost on 2010-05-26
I loves me some Ubuntu, but printing capabilities is a huge reason to not completely switch over from other OS's to Linux.

In the past, I have fought to get a HP 1020 installed.  I won the battle for a couple days.  Out of the blue, the printing capabilities took a dump on me. I didn't have the will to go to battle again.

I am now trying from fresh to install the same HP 1020 on a different computer.  I connected the printer via USB.  The printer was detected and installed some drivers.  I couldn't print even though Ubuntu indicated my print job completed successfully.  I beg to differ as nothing printed.  I then installed the HP Toolbox.  The HP Toolbox is indicating a required plug-in is missing.  I select the radio button to download the plug-in from an authorized HP site.  That is where I sit as the mystery plug-in isn't found.

Ugh.....

Like I said, I loves me some Linux, but printing needs to be easier.  In the past, I would drop my file into Dropbox and then dual boot over to Vista to print.  :(

**off to search the forum for the missing plug-in**

---

### Post by GSF1200S on 2010-05-26
I would recommend installing hplip and cups (which should already be installed):
```
sudo apt-get install hplip
sudo apt-get install cups
```
then run:
```
sudo /etc/init.d/cups restart
```

Then, go to your web browser and put the following in the address bar:
```
http://localhost:631
```
At some point, it will ask you for your username and password. Ensure that the username is
> root
and that the password is the root password. In that web interface, you can try the detect printer option and it should automagically find the proper ppd for you.

---

### Post by finlost on 2010-05-26
Out of the blue, my page printed when I resubmitted it for the fifth time without doing anything additional (such as updating firmware or plugins).

Printing definitely needs to be more streamlined and reliable if Ubuntu/Linux wants to continue growing a user base.

---

