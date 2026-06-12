---
title: "Printer not working"
date: 2009-07-31
forum: New to Ubuntu
---

### Post by Iknownothing on 2009-07-31
Hi All

Now have the Dialogue Box issue resolved, thank you all for your input. I have a new printer for this notebook but can not seem to make it print. in addition I now have an impressive print queue of 36 jobs lined up and can not cancel them...HELP!!! The printer is a HP Deskjet F4272

---

### Post by swoll1980 on 2009-07-31
> **Iknownothing said:**
> Hi All

Now have the Dialogue Box issue resolved, thank you all for your input. I have a new printer for this notebook but can not seem to make it print. in addition I now have an impressive print queue of 36 jobs lined up and can not cancel them...HELP!!! The printer is a HP Deskjet F4272

This is what I've been able to dig up. 

```
sudo apt-get install hplip
```

```
sudo hp-setup
```

give your user password when requested, you don't see nothing when you type it, then press enter.

Here other questions and answers about hplip [https://answers.launchpad.net/ubuntu/+source/hplip](https://answers.launchpad.net/ubuntu/+source/hplip)

Hope this is helpful. :D

---

### Post by Iknownothing on 2009-07-31
Hi 

Thanks for your help, very much appreciated. I do have another question and please do forgive my very low understanding here but where do I type this code into? very nervous about doing this as I feel its beyond me and don't want to break my notebook

---

### Post by Sef on 2009-07-31
> Thanks for your help, very much appreciated. I do have another question and please do forgive my very low understanding here but where do I type this code into? very nervous about doing this as I feel its beyond me and don't want to break my notebookInstead of installing via the command line, install HPLIP this way:

Applications > Add/Remove > Show: All Available Applications > Search: HPLIP > tic the box next to HPLIP Toolbox > Apply Changes > Apply > close

After that go to System > Preferences > HPLIP Toolbox.  Then go to Printer Control (last tab on the right) and see if you delete the print jobs.   Probably nothing will printer until you delete those jobs.

Also your printer is not a desktjet, but an all-in-one.

[HPLIP Website]("http://hplipopensource.com/hplip-web/index.html")

---

### Post by Iknownothing on 2009-07-31
Hi 

Thanks for that, I shall give it a go and report back to you...(deep breath)

Here goes....

---

### Post by Iknownothing on 2009-07-31
> **Sef said:**
> Instead of installing via the command line, install HPLIP this way:

Applications > Add/Remove > Show: All Available Applications > Search: HPLIP > tic the box next to HPLIP Toolbox > Apply Changes > Apply > close

After that go to System > Preferences > HPLIP Toolbox.  Then go to Printer Control (last tab on the right) and see if you delete the print jobs.   Probably nothing will printer until you delete those jobs.

Also your printer is not a desktjet, but an all-in-one.

[HPLIP Website]("http://hplipopensource.com/hplip-web/index.html")

Hi again

Did the first part..no issues.  Second part ok at first but then a box came up and tells me no HP device detected even though the first part told me it had been installed. a device manager asked me to update which I did, no problems, I think anyway. the dialogue box is asking me to set up device or cups web interface, what should I do now?

---

### Post by Sef on 2009-08-01
> Second part ok at first but then a box came up and tells me no HP device detected even though the first part told me it had been installed.

1) Is the printer turned on and plugged (both plug and usb?)

2) If so, and the printer is turned all plugged in and turned on, then Applications > Accessories > Terminal

copy and paste this command in the Terminal:

```
lsusb
```

Copy and paste the results here.

That will show us if your printer is being detected.

---

### Post by la3875 on 2009-08-01
...also please help us help you by letting us know if the printer is directly connected to your computer or you are printing over a home network. It has been my experience with Ubuntu and HP printers that I have the greatest success giving them a static IP address.

Cheers!

---

### Post by Iknownothing on 2009-08-01
> **Sef said:**
> 1) Is the printer turned on and plugged (both plug and usb?)

2) If so, and the printer is turned all plugged in and turned on, then Applications > Accessories > Terminal

copy and paste this command in the Terminal:

```
lsusb
```Copy and paste the results here.

That will show us if your printer is being detected


Hi 

I did that and I think its come up as detected;


.carl@carl:~$ lsusb
Bus 005 Device 004: ID 03f0:2504 Hewlett-Packard 
Bus 005 Device 002: ID 0c45:63e4 Microdia 
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 002: ID 413c:02b0 Dell Computer Corp. 
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
carl@carl:~$ 


Cheers

---

### Post by Iknownothing on 2009-08-01
> **la3875 said:**
> ...also please help us help you by letting us know if the printer is directly connected to your computer or you are printing over a home network. It has been my experience with Ubuntu and HP printers that I have the greatest success giving them a static IP address.

Cheers!


Hi

USB, I did not even know there was another way it could be done! I'm not on the absolute beginners forum for nothing!!!:P

---

### Post by Iknownothing on 2009-08-01
Hi 



.[/quote]carl@carl:~$ lsusb
Bus 005 Device 004: ID 03f0:2504 Hewlett-Packard 
Bus 005 Device 002: ID 0c45:63e4 Microdia 
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 002: ID 413c:02b0 Dell Computer Corp. 
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
carl@carl:~$ 

I did that and I think its come up as detected;
 
Cheers

---

### Post by Iknownothing on 2009-08-01
Hi All

Still unable to get my notebook to print, please read whole thread so you can see where I am with this. very grateful for all suggestions

---

### Post by Sef on 2009-08-02
It looks like it partly detects it; here is mine line from lsusb:

```
Bus 003 Device 002: ID 03f0:5511 Hewlett-Packard Deskjet F300 series

```

Have you checked the [HPLIP]("http://hplipopensource.com/hplip-web/index.html") site for help?

---

### Post by Iknownothing on 2009-08-02
> **swoll1980 said:**
> This is what I've been able to dig up. 

```
sudo apt-get install hplip
``````
sudo hp-setup
```give your user password when requested, you don't see nothing when you type it, then press enter.

Here other questions and answers about hplip [https://answers.launchpad.net/ubuntu/+source/hplip](https://answers.launchpad.net/ubuntu/+source/hplip)

Hope this is helpful. :D

Hi 

Tried both those code. Code 1 said device not powered on etc, which it is.
Code 2 came back with;

carl@carl:~$ sudo apt-get install hplip
Reading package lists... Done
Building dependency tree       
Reading state information... Done
hplip is already the newest version.
hplip set to manually installed.
The following packages were automatically installed and are no longer required:
  libnss3-dev libnspr4-dev
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
carl@carl:~$ 

What we think?

---

### Post by Michl on 2009-08-03
Check the HP site for the HPLIP version
you need.  SOme of the newest printers
need HPLIP 3.9.6 and I believe only
Karmic supplies that driver.  You can
download HPLIP 3.9.6 from the HP site
and install it, BUT I don;t know if that
works in Hardy, Intrepid or Jaunty.
Maybe someone can address that issue.

---

### Post by Iknownothing on 2009-08-05
> **Michl said:**
> Check the HP site for the HPLIP version
you need.  SOme of the newest printers
need HPLIP 3.9.6 and I believe only
Karmic supplies that driver.  You can
download HPLIP 3.9.6 from the HP site
and install it, BUT I don;t know if that
works in Hardy, Intrepid or Jaunty.
Maybe someone can address that issue.

Its in Hardy Heron, still not having any joy here at all!!! I  will try and install 3.9.6 and report back here. I am very open to suggestions.

---

### Post by achase79 on 2009-08-05
You need at least version 2.8.5 and hardy has only 2.8.2.

---

### Post by Iknownothing on 2009-08-09
where do I go now then?

---

### Post by Sef on 2009-08-11
>  		where do I go now then? 	

Go [here]("http://hplipopensource.com/hplip-web/index.html").

---

