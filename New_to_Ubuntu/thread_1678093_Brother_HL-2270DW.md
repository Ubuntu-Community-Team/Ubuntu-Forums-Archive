---
title: "Brother HL-2270DW"
date: 2011-01-29
forum: New to Ubuntu
---

### Post by camelface on 2011-01-29
Hi guys, 

I'm trying to install the drivers of this printer without success. I am a newb at ubuntu so I am trying ways outside the terminal. That is, I tried using the add printer function in the printing menu in administration. It gives me a nice list of printers for which drivers are available but not for my model which I believe is quite new. At least the network picks up the printer though since it is already installed on a few computers in this house. (It is not hooked up to any of the computers, it is standing alone on the wifi). 

I went to the brother website to look at the drivers and there I can download LPR and CUPS drivers but I have no idea what these are. They both come in two forms, either RPM or DEB. I clicked on the LPR deb one and was able to install it because the software centre popped up and I just had to click. The CUPS doesn't install however. I click install and at after the progress bar has finished it doesn't say that the driver is installed. 

I made the two following steps before starting: 

**1. "sudo aa-complain cupsd"** command is required before the installation.[B]
2. "sudo mkdir /usr/share/cups/model"[/B] command is required before the installation.

I understand it is to give me administrator access, however I really don't know what cups or lpr is (do I need to retype these if I restart my computer?). The second is to creatre a directory but I don't know why. I don't think I am too far from getting this complete since the printer is seen on the network, but I need a little help, for which I would be very thankful! 

Have a good weekend, 

David

---

### Post by Girya on 2011-01-29
I just installed my brother printer this morning so I'll try to help you. 

open up a terminal and type or paste in the following command: 

```
dpkg  -l  |  grep  Brother
``` 
 
and post the output. the command checks to see if the driver(s) are installed

the output on my computer shows this, yours will be a little different

> ii  mfc295cncupswrapper                   1.1.2-2                                           Brother CUPS Inkjet Printer Definitions
ii  mfc295cnlpr                           1.1.2-1                                           Brother lpr Inkjet Printer Definitions


---

### Post by camelface on 2011-01-29
this is what I get as output: 

```

ii  cupswrapperhl2270dw                   2.0.4-2                              
           Brother HL2270DW CUPS wrapper driver
ii  hl2270dwlpr                           2.1.0-1                               
           Brother HL-2270DW LPR driver

```I have ubuntu 10.10 by the way. I just upgraded by 10.04 which I found rather buggy but that is another matter of its own...

---

### Post by Girya on 2011-01-29
so the drivers are installed, that's good.

you should be able to find the printer through the system>Administration>printing interface. Reboot your computer and then see if you can find it. in the printing dialog. 

open it up and press the add button. assuming you want to add a networked printer as opposed to one connected locally by a usb cable click on "Network Printer". if your printer is there highlight it and  follow the instructions to add it. post back your results.

---

### Post by camelface on 2011-01-29
Hey Girya, thank you very much for your help. It worked! When I went back in the printing dialog, the drivers were added in the list. I just had to click a few things and I was done. 

For future reference, what are deb and rpm? is deb a file-type conversion for rpm that works in graphical interface?

---

### Post by Girya on 2011-01-29
.deb and .rpm are files for different linux distros package management. deb is for debian derivatives(like ubuntu) that use dpkg package management and rpm is for Red Hat and its derivatives. 

check out some bash terminal tutorials. while learning the terminal can be incredibly frustrating, at least for a caveman like me, the terminal is way better for many things, like ripping dvds(mencoder), email(mutt), manipulating files (copy and moving batches of files) listening to music (cmus) searching (grep and find). 

good luck and I was happy to be of some help.

---

### Post by camelface on 2011-02-11
Hey guys, my printer has been going well with ubuntu and every other windows computer in the house until a few days ago:

I printed a document, and saw the day after that it did not print the whole thing. I go to see the printer and it seems to have been paused with the light flashing. I pressed "Go" twice and it resumed printing but it did not print the whole thing. 

Since then, I have printed with Windows computers without problems. Whenever my ubuntu computer gets a printjob it remains pending forever. When I look at the printing window, it now says that the printer cannot be located (see attachment). 

I find this puzzling as my other computer locate it perfectly and I have network access on the ubuntu computer otherwise. It evens lists my printer in the search network printer function. I just wanted to post this before I delete the printer and reinstall it. I'd like to know what is wrong...

Thanks guys


EDIT: REINSTALLED AND IT WORKS. THREAD MARKED AS SOLVED.

---

### Post by walt.smith1960 on 2011-02-11
I have 2 networked Brother printers.  I've had the best success assigning static I.P. addresses to the printers. In the "device URI" box I enter "socket://xxx.xxx.xxx.xxx:9100" That has worked most reliably for me.  Brother does seem to make their instructions  more complex than necessary.  On the other hand Brother does offer better Linux support than every manufacturer except Hewlett Packard in my opinion.

---

### Post by sbrandon on 2011-02-20
Has anyone been able to attach to this printer via the wireless feature. I'm not sure how to assign an IP address so I don't know if I can force the connection. I am using FIOS router. Thanks

---

### Post by walt.smith1960 on 2011-02-21
> **sbrandon said:**
> Has anyone been able to attach to this printer via the wireless feature. I'm not sure how to assign an IP address so I don't know if I can force the connection. I am using FIOS router. Thanks

I don't have this machine but have you looked at this?  

[http://www.brother-usa.com/ModelDocuments/Consumer/Network%20Users%20Manual/NUM_HL_2270DW_EN_2639.PDF]("http://www.brother-usa.com/ModelDocuments/Consumer/Network%20Users%20Manual/NUM_HL_2270DW_EN_2639.PDF")

The first few pages are Windows/Mac stuff but it looks like starting about page 28 you can print out the machine's network info then log into the web interface and tweak things as you desire.

It looks like BRAdminlight is available for Linux as well if you want to try that:
[http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/instruction_bra1.html](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/instruction_bra1.html)

I hope you find this of some use.

p.s. you'd need a network connection to be able to log onto the web administration page. Catch22--you don't have a network connection. Try plugging a network cable in temporarily?

---

### Post by migs73 on 2011-02-21
> **walt.smith1960 said:**
> I have 2 networked Brother printers.  I've had the best success assigning static I.P. addresses to the printers. In the "device URI" box I enter "socket://xxx.xxx.xxx.xxx:9100" That has worked most reliably for me.  Brother does seem to make their instructions  more complex than necessary.  On the other hand Brother does offer better Linux support than every manufacturer except Hewlett Packard in my opinion.

+1 with the static IP address. That's what I have done with my printer (also a Brother, not that it should matter what type) and haven't had any problems with it.

Brother are great for providing drivers, but their website is incredibly confusing.

---

### Post by walt.smith1960 on 2011-02-23
I agree, Brother's web site isn't the most easily navigated ever.  I did make one pleasant discovery with my MFC-7820N.  When printing multiple pages using FooMatic or BRscript drivers, there was about 20-30 seconds between pages. I installed the CUPS driver from Synaptic then selected it in printer properties.  MUCH faster. I don't know if this is true of the HL series printers or not.

---

### Post by riskylemonz on 2011-05-02
I have Ubuntu 11.4 so this may explain why it hasn't worked for me.  I have the drivers installed,
```
ii  brhl2170wlpr                          2.0.2-1                                    Brother HL-2170W LPR driver
ii  cupswrapperhl2270dw                   2.0.4-2                                    Brother HL2270DW CUPS wrapper driver
ii  hl2270dwlpr                           2.1.0-1                                    Brother HL-2270DW LPR driver

```

but when i go into the printing interface, my HL2270DW doesn't show up.  this is whether the printer is plugged in via network cable or not.

I'm quite new to linux, so any help would be appreciated.

---

### Post by migs73 on 2011-05-04
> **riskylemonz said:**
> I have Ubuntu 11.4 so this may explain why it hasn't worked for me.  I have the drivers installed,
```
ii  brhl2170wlpr                          2.0.2-1                                    Brother HL-2170W LPR driver
ii  cupswrapperhl2270dw                   2.0.4-2                                    Brother HL2270DW CUPS wrapper driver
ii  hl2270dwlpr                           2.1.0-1                                    Brother HL-2270DW LPR driver

```

but when i go into the printing interface, my HL2270DW doesn't show up.  this is whether the printer is plugged in via network cable or not.

I'm quite new to linux, so any help would be appreciated.

The LPR driver showing above is for the 2170 not the 2270. Don't if this is the issue but it looks odd.

Mike :)

---

### Post by riskylemonz on 2011-05-05
hm. didn't notice that.

is there an easy way to uninstall it?  i suppose there would be a terminal command, right?

---

### Post by garvinrick4 on 2011-05-05
Url:
[http://localhost:631/printers](http://localhost:631/printers)
that should bring you to your printers to delete add modify and such.

---

### Post by riskylemonz on 2011-05-05
there aren't any printers showing up here.  would that mean the drivers aren't installed properly?

would it be easier to connect the printer to a Linksys WRT54G and access it that way?  or would that be more problematic?

---

### Post by legatolemans on 2011-10-24
I'm a complete Noob hee trying to install Brother HL-2270DW.  I have Ubuntu 11.10.  I'm not sure if I have the driver installed, and what other steps there are to install the printer. 

Please let me know if you can help :)
thx

This is how far I've got.  I don't understand it

```
dpkg  -l  |  grep  Brother
ii  ptouch-driver                          1.3-0ubuntu11                           CUPS/Foomatic driver for Brother P-touch label printers
```

---

### Post by Justin Baskaran on 2012-07-28
welcome to ubuntu i personally use mint but i used to use ubuntu
 
 
1 go to [http://localhost631](http://localhost631)
 
2 add printer
 
3 get your netowrk ip address by pushing the go button on the printer 3 times the third page 1/4 way down will show your ip address
 
4 add printer according to ipp adress
 
5 copy and paste ip for lpd://xxx.xxx.xxx.xxx 
 
6 add ppd file (i will attach once i get home)
 
7 add printer
 
8 name printer
 
9 click add printer
 
if you need more help you can email this message and i will make a youtube video and send you the link i am very fast at responding 
 
unlike others I KNOW 100% THIS WAY WORKS!!!!

---

### Post by Justin Baskaran on 2012-07-28
> **legatolemans said:**
> I'm a complete Noob hee trying to install Brother HL-2270DW. I have Ubuntu 11.10. I'm not sure if I have the driver installed, and what other steps there are to install the printer. 
 
Please let me know if you can help :)
thx
 
This is how far I've got. I don't understand it
 
```
dpkg  -l  |  grep  Brother
ii  ptouch-driver                          1.3-0ubuntu11                           CUPS/Foomatic driver for Brother P-touch label printers
```
 doesnt work

---

