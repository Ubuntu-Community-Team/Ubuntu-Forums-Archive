---
title: "bloomberg anywhere on ubuntu"
date: 2009-07-25
forum: New to Ubuntu
---

### Post by indra1975 on 2009-07-25
Hello,
I am a newbie to ubuntu having converted my dell inspiron b130 into interpid ibex about 2 weeks back. Everything seems to run fine but one of the tasks that I like to do is to connect to Bloomberg Professional using Bloomberg Anywhere. This feature works well in my IBM work laptop where it uses a citirix client to connect to Bloomberg Professional screens. I use either IE / firefox browsers in my work laptop.
Has anyone installed BBG anywhere on ubuntu(ibex) w/firefox? If so any helpful pointers will be highly appreciated. I read a thread on citrix installations but I am not sure which version of citrix client to install. Bloomberg website is not very helpful and does not explicitly say it supports ubuntu/linux. Let me know if you want me to elaborate on any part of the thread. Once again any help/advice will be highly appreciated.

bests
ic

---

### Post by swoll1980 on 2009-07-25
You could try installing in [Wine.]("winehq.org") Wine is a Window's application compatibility layer for UNIX like operating systems. You can download it from the repos.

---

### Post by indra1975 on 2009-07-25
> **swoll1980 said:**
> You could try installing in [Wine.]("http://winehq.org") Wine is a Window's application compatibility layer for UNIX like operating systems. You can download it from the repos.

Thanks for the tip...I looked up wine from the synaptic package manager and it looks like I can install it without additional help. However, Ubuntu is the only o/s in my laptop, so if wine needs any windows files from a partition or something then I won't have any. Is that going to be a problem?

---

### Post by llamabr on 2009-07-25
wine is very rarely the correct solution (tho the answer to your question is that you'll need all those dll files from somewhere else).

I can't figure out quite what bloomberg professional is.  Is it just a web app?  Or another program?

Possibly, there's a native application that does what you want.

---

### Post by indra1975 on 2009-07-26
> **llamabr said:**
> wine is very rarely the correct solution (tho the answer to your question is that you'll need all those dll files from somewhere else).

I can't figure out quite what bloomberg professional is.  Is it just a web app?  Or another program?

Possibly, there's a native application that does what you want.

Bloomberg (BBG) is a proprietary financial data feed/network used by pros to get real time quotes, market data, news and make trades. I believe it is built on a mainframe system and was originally used for trading fixed income bonds. At work our laptops become BBG "terminals" with its own keyboard, multi screens etc. However there is also an option to connect to BBG using a browser...it will prompt for a citrix client installation and once the authentication is successful it will pop up the familiar four BBG screens. 
Hope this gives some briefing about BBG. Will wine be able to tell me all the needed dll files? if so i could copy them from my work laptop..is that a feasible approach?

---

### Post by mikechant on 2009-07-27
Wine can tell you what dlls are missing, but the chances of it running even then are not that good (not even listed at winehq). If it doesn't work, your best option may be running it in Windows in a VM.

---

### Post by llamabr on 2009-07-27
Right.  I'm not familiar with this software (obviously), but I don't think this will work.  If it's complicated, and it was written to run on windows, then your best bet is to run it on windows.  Wine will run some simple things, sometimes, but it's almost never the correct solution to a real problem.

Contact the tech people there and ask if they have a native unix app.

---

### Post by indra1975 on 2009-07-27
> **llamabr said:**
> Right.  I'm not familiar with this software (obviously), but I don't think this will work.  If it's complicated, and it was written to run on windows, then your best bet is to run it on windows.  Wine will run some simple things, sometimes, but it's almost never the correct solution to a real problem.

Contact the tech people there and ask if they have a native unix app.
Thank you for your suggestions.

---

### Post by Durden on 2009-07-27
No reason not to try wine. I've gotten some crazy stuff to work with it. BBG is pretty basic stuff really.

You mentioned it works in a web browser? If so I don't see why it wont work in Linux Firefox, unless by "works in a browser" means it calls outside programs.

If it doesnt work in wine or Fireox for you then go to synaptic and get VirtualBox installed. Install windows inside VirtualBox and do your BBG stuff in there. You take a performance hit but BBG doesn't sound like th emost resource intensive app out there. VBox should be fine. If VirtualBox isn't to your liking you can also try VMware which is basically the same thing but maybe better supported.

---

### Post by gunksta on 2009-07-27
But I'm not sure FF on Linux can use the Citrix stuff. I've seen that before where it required ActiveX, which we definitely don't have.

---

### Post by Durden on 2009-07-27
Well if it's working on Windows in FF then it's not using active-x for that. I've never done the Citrex thing so I can't be sure what they are doing.

---

### Post by gunksta on 2009-07-28
> **Durden said:**
> Well if it's working on Windows in FF then it's not using active-x for that. I've never done the Citrex thing so I can't be sure what they are doing.


Hmm. Good point.

---

### Post by indra1975 on 2009-07-30
> **Durden said:**
> No reason not to try wine. I've gotten some crazy stuff to work with it. BBG is pretty basic stuff really.

You mentioned it works in a web browser? If so I don't see why it wont work in Linux Firefox, unless by "works in a browser" means it calls outside programs.

If it doesnt work in wine or Fireox for you then go to synaptic and get VirtualBox installed. Install windows inside VirtualBox and do your BBG stuff in there. You take a performance hit but BBG doesn't sound like th emost resource intensive app out there. VBox should be fine. If VirtualBox isn't to your liking you can also try VMware which is basically the same thing but maybe better supported.

I have'nt tried wine yet but I am speaking to a BBG rep next week...will ask her if she has a workaround for this...The VirtualBox or VMware sounds like a plausible solution too...I will keep you posted on developments.
I think BBG from a browser does call outside programs, it keeps looking for a "citrix client"...

---

### Post by odensen on 2009-08-09
you need to go to package manager and load the java run-time environment JE5 or higher should work

---

### Post by y-lee on 2009-08-09
> **indra1975 said:**
> I think BBG from a browser does call outside programs, it keeps looking for a "citrix client"...

I know nothing about Citrix clients or BBG, but it seems there is a [Citrix client for linux]("http://www.citrix.com/site/SS/downloads/details.asp?dID=2755&downloadID=3323").

---

### Post by indra1975 on 2009-08-15
> **indra1975 said:**
> I have'nt tried wine yet but I am speaking to a BBG rep next week...will ask her if she has a workaround for this...The VirtualBox or VMware sounds like a plausible solution too...I will keep you posted on developments.
I think BBG from a browser does call outside programs, it keeps looking for a "citrix client"...

According to BBG reps, I have to install citrix XenApp client for Linux and that should do the trick. Now if I go to citrix site [http://www.citrix.com/English/ss/downloads/details.asp?downloadId=3323&productId=186&c1=sot2755&c2=ost1349860](http://www.citrix.com/English/ss/downloads/details.asp?downloadId=3323&productId=186&c1=sot2755&c2=ost1349860)
it calls for openmotif also.

Has anyone here installed the XenApp client and if so can they please guide me towards the installation? Also if they could clarify about openmotif that would be helpful too.

Looking fwd to your replies..

best wishes
ic

---

### Post by odensen on 2009-10-16
i have bloomberg anywhere working on ubuntu.   install JE5 through the package manager.  then install citrux software.  if this is not enough information, i will reconstruct what i did for you.

---

### Post by filifunk on 2010-08-24
> **odensen said:**
> i have bloomberg anywhere working on ubuntu.   install JE5 through the package manager.  then install citrux software.  if this is not enough information, i will reconstruct what i did for you.

What is JE5?  Or could you or someone reconstruct this for me?  Thanks.  I tried looking up JE5 in the package manager and I don't have it.  Is it a Java thing?

---

### Post by Vaphell on 2010-08-24
look for jre, #14 said java runtime environment

---

### Post by BomBom on 2010-09-23
Ubuntu Lucid

Albeit I prefer Chrome as browser, I could get BBG Anywhere to work with Firefox only.
I downloaded Citrix for Linux (version 11.100 .deb file on [http://www.citrix.com/English/ss/downloads/details.asp?downloadId=3323&productId=186&c1=sot2755&c2=ost1349860#top](http://www.citrix.com/English/ss/downloads/details.asp?downloadId=3323&productId=186&c1=sot2755&c2=ost1349860#top))

and I found OpenMotif (openmotif_2.3.3-1_lucid_i386.deb) on [http://www.motifzone.net/filebrowser/openmotif/2.3/2.3.3](http://www.motifzone.net/filebrowser/openmotif/2.3/2.3.3)

Please note that I could not get the Java version to run: on the first login screen of Bloomberg Anywhere ([https://bba.bloomberg.net/default/auth/login.aspx](https://bba.bloomberg.net/default/auth/login.aspx)) I chose 'Native'.

Good luck!

---

