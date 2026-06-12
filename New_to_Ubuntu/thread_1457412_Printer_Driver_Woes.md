---
title: "Printer Driver Woes"
date: 2010-04-18
forum: New to Ubuntu
---

### Post by LittleFrank on 2010-04-18
I'm new to Linux (Ubuntu) and trying to install a printer driver.

I have a Samsung SCX 4826FN for which Samsung provides a Linux "Unified Driver"along with vague instructions for installing it. 

Those instructions tell me to Open "Root Terminal" which I think I figured out how to do - I can get a prompt with a #.

Unfortunately the next step - "3. Execute installation program. $ sudo cdroot/autorun" - results in nothing but "command not found". I've tried omitting the $ and I get the same result. If I omit the both the $ and sudo portion I get "No such file or directory" I can see the directory and file on my hard drive so I know it is there.

I have tried the same steps from the $ prompt but get the same results. I guess I don't know why Smasung tells me to Open "Root Terminal" and then tells me to use the sudu command from a # prompt. Seems these instructions were poorly thought out and not tested by the manufacturer.

Here are the complete instructions:

[Ubuntu OS Installation]

1. Download and extract the driver 

2. Open ''Root Terminal'' 

3. Execute installation program. 

   $ sudo cdroot/autorun

4. After install, PPD path is set again.

   $ sudo ln -s /usr/share/cups/model/samsung /usr/share/ppd/custom/samsung

5. Execute Configurator, and Add your printer model name by Add Printer

Can anyone be so kind as to tell this hapless fool how to interpret these instructions and install my printer? Again, I can't get past step 3.:confused:
 		                   		  		  		  		  		  	   	 		 [IMG]http://ubuntuforums.org/images/statusicon/user_online.gif[/IMG]  		 		 		[[IMG]http://ubuntuforums.org/images/buttons/report.gif[/IMG]]("http://ubuntuforums.org/report.php?p=9140453") 		 		  	 	 	 	 		  		 			[IMG]http://ubuntuforums.org/images/misc/progress.gif[/IMG] 			[[IMG]http://ubuntuforums.org/images/buttons/edit.gif[/IMG]]("http://ubuntuforums.org/editpost.php?do=editpost&p=9140453")

---

### Post by sandyd on 2010-04-18
> **LittleFrank said:**
> I'm new to Linux (Ubuntu) and trying to install a printer driver.

I have a Samsung SCX 4826FN for which Samsung provides a Linux "Unified Driver"along with vague instructions for installing it. 

Those instructions tell me to Open "Root Terminal" which I think I figured out how to do - I can get a prompt with a #.

Unfortunately the next step - "3. Execute installation program. $ sudo cdroot/autorun" - results in nothing but "command not found". I've tried omitting the $ and I get the same result. If I omit the both the $ and sudo portion I get "No such file or directory" I can see the directory and file on my hard drive so I know it is there.

I have tried the same steps from the $ prompt but get the same results. I guess I don't know why Smasung tells me to Open "Root Terminal" and then tells me to use the sudu command from a # prompt. Seems these instructions were poorly thought out and not tested by the manufacturer.

Here are the complete instructions:

[Ubuntu OS Installation]

1. Download and extract the driver 

2. Open ''Root Terminal'' 

3. Execute installation program. 

   $ sudo cdroot/autorun

4. After install, PPD path is set again.

   $ sudo ln -s /usr/share/cups/model/samsung /usr/share/ppd/custom/samsung

5. Execute Configurator, and Add your printer model name by Add Printer

Can anyone be so kind as to tell this hapless fool how to interpret these instructions and install my printer? Again, I can't get past step 3.:confused:
 
They made a small typo, in step 3.
replace "/path/to/downloaded/files/" with the directory where you extracted the installer
for example, if you extracted it to your desktop, and the folder is called "X", you would do "cd ~/Desktop/X"
```

cd /path/to/downloaded/files/
sudo sh ./autorun

```

---

### Post by LittleFrank on 2010-04-18
Thanks.

The Tilda (~) got me to a point where I can at least run the Installer, but unfortunately it does not recognize my printer. I've installed it manually to every port listed with no success.

Very exasperating. 

Oh well - I guess I continue to beat my head against the wall because doing so sure feels better than giving Microsoft any more money. 

I liken the release of Windows 7 to Ford offering to SELL you a new set of tires after you've rolled your SUV and subsequently suffered the death of your entire family.

---

