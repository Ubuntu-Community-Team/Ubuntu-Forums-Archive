---
title: "ubuntu 10.04.1 somebody outhere who mamaged to get googlearth running in lucid ?"
date: 2010-10-04
forum: New to Ubuntu
---

### Post by okkie on 2010-10-04
can anybody please help me to get googlearth running on my computer.Running 10.04 and could over the past few years manage to solve most problems but apparenly not this one.Is there a standard script i can run in a terminal to kill the "child process" problem which nobody seems to know about?
Thanks

---

### Post by Detonate on 2010-10-04
Follow the instructions here.  Use the instructions for make-googleearth-package.

[https://help.ubuntu.com/community/GoogleEarth](https://help.ubuntu.com/community/GoogleEarth)

---

### Post by realzippy on 2010-10-04
or run this command:

```
sudo wget --output-document=/etc/apt/sources.list.d/medibuntu.list http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list && sudo apt-get --quiet update && sudo apt-get --yes --quiet --allow-unauthenticated install medibuntu-keyring && sudo apt-get --quiet update && sudo apt-get install googleearth
```

---

### Post by okkie on 2010-10-04
thanks a lot to both of you.I tried both your methods without luck.I took screenshots of both outcomes and attach for your perusal.Personally i think the 'child process' is the culprit as i had the problem a few years ago and remember running 'dont know what' in a terminal to fix it.

---

### Post by okkie on 2010-10-04
screenshots mentioned above.Thanks

---

### Post by Detonate on 2010-10-04
Open your file browser and navigate to the folder where the .deb file is located.  Double click on the file and it should open with gdebi and install.  Its probably in your home directory.  Make sure gdebi is installed first.

```
sudo apt-get install gdebi
```

---

### Post by realzippy on 2010-10-04
> **okkie said:**
> thanks a lot to both of you.I tried both your methods without luck.I took screenshots of both outcomes and attach for your perusal.Personally i think the 'child process' is the culprit as i had the problem a few years ago and remember running 'dont know what' in a terminal to fix it.
sorry,what is the whole output from the command:
```
sudo wget --output-document=/etc/apt/sources.list.d/medibuntu.list http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list && sudo apt-get --quiet update && sudo apt-get --yes --quiet --allow-unauthenticated install medibuntu-keyring && sudo apt-get --quiet update && sudo apt-get install googleearth

```

??I only can see "permission denied" on the screenshot.

---

### Post by okkie on 2010-10-04
Realzippy sorry I can't get back to the screenshot.

I have now gone to my homefolder,found the .deb file and installed it.Tried to 'Detonate' it but still no go.Gives Google splash screen and no more.
At least the 'child process' denial thing is gone.
So to summerise, I have GE installed from the .deb file and deleted all other copies of GE i had on my machine to eliminate any possible interference and now only to find out why it gives the splash screen and then fade away.Please see if you can find out what that is.
Thanks

---

### Post by beew on 2010-10-04
Forget about the make-googleearth package and the deb files. Delete the .deb files from your /home folder.

The best and easiest way would be to add the Medibuntu ppa, update, and then install through Synaptic and that's it. Have done it many times, never failed.

You should get rid of everything you have installed. Try 
```
sudo apt-get purge googleearth
``` and use Synaptic to install it again.

---

### Post by k3lt01 on 2010-10-05
> **beew said:**
> Forget about the make-googleearth package and the deb files. Delete the .deb files from your /home folder.

The best and easiest way would be to add the Medibuntu ppa, update, and then install through Synaptic and that's it. Have done it many times, never failed.

You should get rid of everything you have installed. Try 
```
sudo apt-get purge googleearth
``` and use Synaptic to install it again.+1

Always use the official repos, unless you are willing to have big problems, to avoid issues just like this.

---

### Post by Detonate on 2010-10-05
Yes, install from Synaptic is the preferred way.  With the medibuntu repositories enabled.  The only advantage to using the other method is, that you get the latest version.

---

### Post by okkie on 2010-10-06
I have done everythind as you suggest but still no luck.Splash screen appears and disappears.I have had Googlearth for years so it cannot be my system.
I upgraded to 10.04 via the internet,might that have anything to do with the problem?

---

### Post by k33bz on 2010-10-06
The way I did it was download the source and installed it from source.

have you tried what was mentioned above

> **Detonate said:**
> Yes, install from Synaptic is the preferred way.  With the medibuntu repositories enabled.  The only advantage to using the other method is, that you get the latest version.

---

### Post by sydbat on 2010-10-06
> **okkie said:**
> I have done everythind as you suggest but still no luck.Splash screen appears and disappears.I have had Googlearth for years so it cannot be my system.
I upgraded to 10.04 via the internet,might that have anything to do with the problem?The question that has not been asked yet - what are your computer specs? If your graphics card, processor, RAM, etc is insufficient to run the latest Google Earth + Ubuntu 10.04, that might be the problem.

I have had to upgrade a few client's graphics cards (to nVidia) + more RAM  in order for GE to run successfully.

---

### Post by k3lt01 on 2010-10-06
Compiz can really stuff Google Earth around, if you have it installed try removing it and then re-installing GE.

---

### Post by philinux on 2010-10-06
> **k3lt01 said:**
> Compiz can really stuff Google Earth around, if you have it installed try removing it and then re-installing GE.

I think you mean just disable compiz. Sys,Prefs,Appearance, visual effects > none.

---

### Post by k3lt01 on 2010-10-06
> **philinux said:**
> I think you mean just disable compiz. Sys,Prefs,Appearance, visual effects > none.
Nope, I mean remove it.

However, if the OP wants to disable it you have told them how. I myself see no use to eye candy that has to be disabled and then re enabled just so you can use a popular program.

---

### Post by cap10Ibraim on 2010-10-06
I used to have the same problem but today it worked 
on Ubuntu 10.04 64 bit , here are my settings :
1.before from System->administration->software resources->in the first tab , I have the first 2 boxes checked (that will update some qt libraries , go to update manager check , then update 
2.I downloaded the latest version 5.2 (I guess) a .bin file from [http://www.google.com/earth/index.html]("http://www.google.com/earth/index.html")
3.right click the file ->properties->permission tab->check allow executing 
4.drag and drop the file in the terminal

---

### Post by okkie on 2010-10-07
I have done exactly as you prescribed.Splash screen comes up and disappears.It is only since internet upgrade to 10.04 that I have a problem with googlearth.Could that be the reason? Am I the only one?

---

### Post by cap10Ibraim on 2010-10-07
> Google Earth™ — Qt - A cross-platform application and UI framework
What qt libraries do you have ? 
mine :

---

### Post by Cpierce on 2010-10-07
Purge googleearth as describe above, and download the Medibuntu deb package at the bottom of the page here : 
[http://packages.medibuntu.org/lucid/googleearth.html](http://packages.medibuntu.org/lucid/googleearth.html)

and use gdebi package installer. should work, but then again so should the medibuntu command mentioned earlier. If I downloaded from the google site and installed with "sh", it didn't work for me in 10.04, but the medibuntu package did. Make sure you try to run it a couple of times before you give up on it. I have had it quit on the first startup, but then work fine after that.

---

### Post by karlm on 2010-10-07
I have similar problems - I get to the splash screen and then it dies for no apparent reason. 

I read on here that GE has issues with ATI cards, which is what is my laptop - other specs should be more than sufficient.

(60gb HD space remaining, 2GB RAM)

---

### Post by okkie on 2010-10-07
sorry Cap10,I did not know after 10 messages on a page you must go to the next page.
I downloaded the bin file,pasted it into the terminal,it started installing and then told me its a bug.
See attached screenshot.What i do not understand is how a bug can after all these months not be sorted out and why is there not a 'sticky' right at beginners talk to tell us about it.I am in my sixties and have waisted hours of what I have left to find this out.
Thank you and everybody and please tell me if there is a other possibility somewhere.

---

### Post by oldos2er on 2010-10-07
You can file a bug report here: [http://code.google.com/p/earth-issues/issues/list](http://code.google.com/p/earth-issues/issues/list) , click New Issue.

---

### Post by okkie on 2010-10-08
If my ATI card is the problem it means no GE for some time as I cannot afford a new card at this time.Its just funny that my card worked just fine all along till now with GE but since upgrade to 10.04 its non functional or not good enough.Should these problems not be taken care of before new distributions are made available? What awaits us with 10.10 coming?

---

### Post by alphacrucis2 on 2010-10-08
> **karlm said:**
> I have similar problems - I get to the splash screen and then it dies for no apparent reason. 

I read on here that GE has issues with ATI cards, which is what is my laptop - other specs should be more than sufficient.

(60gb HD space remaining, 2GB RAM)

If you run googleearth from the terminal, it should give some message indicating why it crashed. Typical are signal 6 and signal 11.

---

### Post by beew on 2010-10-08
> **okkie said:**
> If my ATI card is the problem it means no GE for some time as I cannot afford a new card at this time.Its just funny that my card worked just fine all along till now with GE but since upgrade to 10.04 its non functional or not good enough.Should these problems not be taken care of before new distributions are made available? What awaits us with 10.10 coming?

Have you actually tried to simply add Medibuntu's ppa to your sources list and let Synaptic does the job? From what I read you are installing deb files, downloading bin files and what not and then get yourself tangled into knot and I am not sure why you insist on doing thingts the hard way (which don't work)

And don't listen to the guy who told you to compile from source, that is insane advice to beginers.

---

### Post by alphacrucis2 on 2010-10-08
> **okkie said:**
> If my ATI card is the problem it means no GE for some time as I cannot afford a new card at this time.Its just funny that my card worked just fine all along till now with GE but since upgrade to 10.04 its non functional or not good enough.Should these problems not be taken care of before new distributions are made available? What awaits us with 10.10 coming?

For me, the medibuntu version did work with 10.4 and ATI card but some update occurred to Lucid over the last couple of months that broke it. Possibly an update to the catalyst driver. It crashes with a signal 6 error for me after displaying the splash screen. When I purge that and install 5.2 googleearth via sudo apt-get googleearth-package and install the deb, it doesn't even get as far as the splash screen. It complains with the following:

```
laptop:~$ googleearth
/usr/lib/googleearth/googleearth-bin: error while loading shared libraries: libphonon.so.4: cannot open shared object file: No such file or directory
```

On my lappy libphonon.so.4 is present in /usr/lib as a link to libphonon.so.4.4.0 which does exist. So I am a bit baffled at present. I plan to upgrade to Maverick in a couple of weeks and I will try the Medibuntu version of googleearth for Maverick once that is available.

---

### Post by k3lt01 on 2010-10-08
My father's Acer laptop is an AMD64 with an ATI card running 10.04.1 and GE works perfectly. It seems to me that the OP needs to wipe all traces of GE of their PC and start again using the Medibuntu Repo version. Compiling source and doing everything else we have been told has been done will have made a huge jumble that will take a bit of work to fix.

---

### Post by alphacrucis2 on 2010-10-08
> **k3lt01 said:**
> My father's Acer laptop is an AMD64 with an ATI card running 10.04.1 and GE works perfectly. It seems to me that the OP needs to wipe all traces of GE of their PC and start again using the Medibuntu Repo version. Compiling source and doing everything else we have been told has been done will have made a huge jumble that will take a bit of work to fix.

Is he running the Catalyst driver or OSS driver. If the Catalyst driver, which version? As I said, googleearth was working perfectly for me until some time over the last few weeks. I hadn't used it for a while when I discovered that it was broken so I haven't identified the exact cause.

---

### Post by k3lt01 on 2010-10-08
I shall check it in the morning for you and post back after I find out the driver.

We were in GE only a couple of days ago. I was showing him how to enable street view so he could take a look at the houses he lived in 60 years ago when he was growing up in the old country.

---

### Post by okkie on 2010-10-10
all I can do at this stageis sit back and watch your posts.I am sure one of you will find the answer.Goodluck

---

### Post by fooman on 2010-10-10
didn't see it mentioned,  but have you tried deleting the hidden .googleearth file in your home directory?

i would suggest purging google earth like described earlier (do it again just to make sure)....then open nautilus and in the toolbar, go to "view" and put a check next to "show hidden files"

find .googleearth, right-click on it and move to trash.

reinstall googleearth and try again.  hope that helps.

---

