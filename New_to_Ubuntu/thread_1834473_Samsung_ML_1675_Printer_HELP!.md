---
title: "Samsung ML 1675 Printer HELP!"
date: 2011-08-27
forum: New to Ubuntu
---

### Post by Emora on 2011-08-27
Hi, I just bought a Samsung ML 1675 and Don't know how to install the driver from the samsung website. I don't know how to log in as root user on terminal nor do I know how to access the auto run. 
(driver is on this page. [http://www.samsung.com/sg/consumer/pc-peripherals-printer/printer-multifunction/mono-laser-printer/ML-1670/XSS/index.idx?pagetype=prd_detail&tab=support](http://www.samsung.com/sg/consumer/pc-peripherals-printer/printer-multifunction/mono-laser-printer/ML-1670/XSS/index.idx?pagetype=prd_detail&tab=support)) 

Really would appreciate any help! 
THANKS

---

### Post by Rex Bouwense on 2011-08-27
Just download the Linux version of the driver that is on the website.  It looks to be in a zip file.
You don't need to log in as root, just precede you commands with sudo.  You will be asked for your password which you will enter.  There will be no indication that anything is happening until you hit enter and then you will be given temporary root privileges.

---

### Post by Emora on 2011-08-28
> **Rex Bouwense said:**
> Just download the Linux version of the driver that is on the website.  It looks to be in a zip file.
You don't need to log in as root, just precede you commands with sudo.  You will be asked for your password which you will enter.  There will be no indication that anything is happening until you hit enter and then you will be given temporary root privileges.


What would be the commands exactly to install it? I'm so lost :s

---

### Post by Emora on 2011-08-30
bump.

---

### Post by Rex Bouwense on 2011-08-30
Right click on the file to unzip it.  Extract the files there.  If unsure select the read me file
Are you sure that your printer isn't recognized by Ubuntu already?

This site may provide you with additional information:
[https://help.ubuntu.com/community/FileCompression](https://help.ubuntu.com/community/FileCompression)

---

### Post by Emora on 2011-09-01
> **Rex Bouwense said:**
> Right click on the file to unzip it.  Extract the files there.  If unsure select the read me file
Are you sure that your printer isn't recognized by Ubuntu already?

This site may provide you with additional information:
[https://help.ubuntu.com/community/FileCompression](https://help.ubuntu.com/community/FileCompression)

I've done that but I don't know the terminal commands to install it. the extracted files are on my desktop. And my printer model is NOT already recognized by Ubuntu. There are other samsung models that are, but mine isn't. Samsung has the driver, I just don't know the terminal commands to install it.

Samsung provides a guide to install here: [http://skp.samsungcsportal.com/integrated/popup/FaqDetailPopup.jsp?cdsite=sg&seq=280079](http://skp.samsungcsportal.com/integrated/popup/FaqDetailPopup.jsp?cdsite=sg&seq=280079)
When I type in the "sudo cdroot/autorun" it asks for password, i type that in, and then it comes up "command not found" 
(yes, I did mark autorun as an executable file and the cdroot folder)
???

---

### Post by Azdour on 2011-09-02
Hi,

When you run the command are you in the directory where the cdroot directory lives?

You may also want to try:

```
sudo ./cdroot/autorun
```

I'm assuming autorun is a file?

---

### Post by Emora on 2011-09-03
> **Azdour said:**
> Hi,

When you run the command are you in the directory where the cdroot directory lives?

You may also want to try:

```
sudo ./cdroot/autorun
```I'm assuming autorun is a file?


It is on my desktop and autorun is a file

---

### Post by DeathByLinux on 2011-09-06
Hello Emora,
             just follow these steps and you should be on your way. I am going to be as thorough as possible.

Step 1: Download the unified driver (UnifiedLinuxDriver_0.92.tar.gz).

Step 2: Open and extract the "cdroot" folder on to your Desktop for convenient interaction. By "extract", I simply mean for you to open the .tar.gz  by double clicking it and then drag the "cdroot" folder on to your Desktop.

Step 3: Open terminal and get the line to Desktop. So, this part is the only tricky part that I could foresee for you. To do this, you need to type "cd /home/(your user name)/Desktop". Note: This is a case and space sensitive procedure. I will write it even clearer to be thorough: "cd(space)/home/username/Desktop"
If you type this in correctly, your next line should read your name and end with "~/Desktop$". This means that you can now interact with objects on your desktop.
Step 4: Type in the following command "sudo cdroot/autorun". This will trigger the autorun and you can just follow the steps. 

I am not sure exactly how new your are to Linux, but your only challenge is in the third step. The actual command to start the autorun is simple (sudo cdroot/autorun). 
Let me know how it turns out, friend.
-DeathbyLinux

---

### Post by Emora on 2011-09-20
So I've gotten the Driver installed but it still doesn't seem to connect. How Do i make sure the device URL has selected the right USB port im using for it? 
It also asks for an authentication password for a test page... but I dont have one?

---

### Post by avantgardaclue on 2011-09-20
> **Emora said:**
> So I've gotten the Driver installed but it still doesn't seem to connect. How Do i make sure the device URL has selected the right USB port im using for it? 
It also asks for an authentication password for a test page... but I dont have one?

Looks like the problems I had, however these instructions worked for my ML1865 and should work for you, i think!

> Getting Samsung ML-1865 Black Mono Laser Printer to work
Just bought one of these nifty laser printers and struggled like mad to get it to work until I sussed how to do it and it was simplicity itself!

Process....

Add to repositories under update manager...

deb [http://www.bchemnet.com/suldr/](http://www.bchemnet.com/suldr/) debian extra

Then get the apt-key

Refresh your repository listings

Go to synaptic and do search for... samsungmfp

Install samsungmfp-data & samsungmfp-driver

Plug in, turn on samsung laser and presto should work!!

More info at [http://www.bchemnet.com/suldr/](http://www.bchemnet.com/suldr/)

---

