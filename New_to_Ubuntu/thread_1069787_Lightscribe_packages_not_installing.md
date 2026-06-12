---
title: "Lightscribe packages not installing?"
date: 2009-02-14
forum: New to Ubuntu
---

### Post by cptrohn on 2009-02-14
Hi, I have a lightscribe enabled drive and I was just trying to install the deb packages for this from the documentaion pages and I get an error that I can't do it because something isn't enabled..

Do I need to enable deb packages to get this done?  Or is there something else I am doing wrong?

Do I need to do this from the command line?  I am running 8.10 and I added the KDE4 desktop to my reg. Ubuntu 8.10..

---

### Post by cerealtx on 2009-02-14
> **cptrohn said:**
> Hi, I have a lightscribe enabled drive and I was just trying to install the deb packages for this from the documentaion pages and I get an error that I can't do it because something isn't enabled..

Do I need to enable deb packages to get this done?  Or is there something else I am doing wrong?

Do I need to do this from the command line?  I am running 8.10 and I added the KDE4 desktop to my reg. Ubuntu 8.10..

copy and paste what error your getting will help us help you

---

### Post by cptrohn on 2009-02-14
The error I'm getting is:```
Download error /tmp/lightscribe-1.18.1.1-linux-2.6-intel-1.d could not be opened because the associated helper application does not exist. change the association in your preferences
```

This is an error that I have never gotten before in anything I've tried to download... Is there a package in the synaptic package manager for lightscribe to make this easier?

---

### Post by 2hot6ft2 on 2009-02-14
Looks like you are missing the last 2 letters of the filename "lightscribe-1.18.1.1-linux-2.6-intel-1.d" should be "lightscribe-1.18.1.1-linux-2.6-intel-1.d[COLOR="Blue"]eb[/COLOR]"

Also I take it you're doing it from a how to and the version may have changed. It's better to go to [http://www.lightscribe.com/downloadSection/index.aspx](http://www.lightscribe.com/downloadSection/index.aspx) and follow the instructions there for downloading and installing the debs.

You will need "2" debs from there and they have to be installed in order. There is also an agreement you have to accept before downloading them.

You'll need the
LIGHTSCRIBE SYSTEM SOFTWARE which is lightscribe-1.18.1.1-linux-2.6-intel.deb which has to be installed first
and also the
LIGHTSCRIBE SIMPLE LABELER which is lightscribeApplications-1.10.19.1-linux-2.6-intel.deb

The instructions for installing are at the bottom of the download pages.

---

### Post by cptrohn on 2009-02-14
> **2hot6ft2 said:**
> Looks like you are missing the last 2 letters of the filename "lightscribe-1.18.1.1-linux-2.6-intel-1.d" should be "lightscribe-1.18.1.1-linux-2.6-intel-1.d[COLOR="Blue"]eb[/COLOR]"

Also I take it you're doing it from a how to and the version may have changed. It's better to go to [http://www.lightscribe.com/downloadSection/index.aspx](http://www.lightscribe.com/downloadSection/index.aspx) and follow the instructions there for downloading and installing the debs.

You will need "2" debs from there and they have to be installed in order. There is also an agreement you have to accept before downloading them.

You'll need the
LIGHTSCRIBE SYSTEM SOFTWARE which is lightscribe-1.18.1.1-linux-2.6-intel.deb which has to be installed first
and also the
LIGHTSCRIBE SIMPLE LABELER which is lightscribeApplications-1.10.19.1-linux-2.6-intel.deb

The instructions for installing are at the bottom of the download pages.

Actually the lightscribe site is where I attempted the download from...Which is why I can't for the life of me figure out what is wrong... I think there is another download from the HP website that I might give a try that might be the fix for me since my laptop is from HP and i think I remember seeing something about this before but my search of the forums didn't turn the thread up I was searching for..

---

### Post by 2hot6ft2 on 2009-02-14
The lightscribe software will allow you to print text in a circular area around the disc but not any pictures.

If you want to print a picture on discs then you will want the LaCie LightScribe Labeler which works good for pictures but not for text.

So really if you want to do both pictures and text you'll want both.

LaCie LightScribe Labeler is available here: [http://www.lacie.com/us/support/drivers/driver.htm?id=10094](http://www.lacie.com/us/support/drivers/driver.htm?id=10094)

The LaCie software also requires that the
LIGHTSCRIBE SYSTEM SOFTWARE which is lightscribe-1.18.1.1-linux-2.6-intel.deb has to be installed first.

---

### Post by cptrohn on 2009-02-14
> **2hot6ft2 said:**
> The lightscribe software will allow you to print text in a circular area around the disc but not any pictures.

If you want to print a picture on discs then you will want the LaCie LightScribe Labeler which works good for pictures but not for text.

So really if you want to do both pictures and text you'll want both.

LaCie LightScribe Labeler is available here: [http://www.lacie.com/us/support/drivers/driver.htm?id=10094](http://www.lacie.com/us/support/drivers/driver.htm?id=10094)

The LaCie software also requires that the
LIGHTSCRIBE SYSTEM SOFTWARE which is lightscribe-1.18.1.1-linux-2.6-intel.deb has to be installed first.

Yeah, but I keep getting the same error when I download the deb file for the Lightscribe System File...When I click the download file it tries to open with the deb installer... Is there a way to do this from a terminal that you know of?  For some reason just hitting the download link doesn't seem to be working for me at this point.

---

### Post by 2hot6ft2 on 2009-02-14
> **cptrohn said:**
> Actually the lightscribe site is where I attempted the download from...Which is why I can't for the life of me figure out what is wrong... I think there is another download from the HP website that I might give a try that might be the fix for me since my laptop is from HP and i think I remember seeing something about this before but my search of the forums didn't turn the thread up I was searching for..
Ok, but HP will have the windows version and not the Linux version of the software.

Also the filename you were using is not current or complete so that is the problem.

Looks like you are missing the last 2 letters of the filename "lightscribe-1.18.1.1-linux-2.6-intel-1.d" should be "lightscribe-1.18.1.1-linux-2.6-intel-1.d[COLOR="Blue"]eb[/COLOR]"
And the current version is
lightscribe-1.18.1.1-linux-2.6-intel.deb
not
lightscribe-1.18.1.1-linux-2.6-intel[COLOR="Blue"]-1[/COLOR].deb

On another point both the lightscribe and the LaCie software are for 32 bit OS's.

---

### Post by 2hot6ft2 on 2009-02-14
Right click on it and use "Save Link As" to save it to your drive somewhere.

Since it has the agreement that you have to accept before you can download it I suspect it may not work as a direct download from a terminal.

But here is the link to the download you can just right click on it and do the same thing so replacing the info in the commands you were using with the right link info should work just as well. [http://download.lightscribe.com/ls/lightscribe-1.18.1.1-linux-2.6-intel.deb](http://download.lightscribe.com/ls/lightscribe-1.18.1.1-linux-2.6-intel.deb)

---

### Post by cptrohn on 2009-02-14
> **2hot6ft2 said:**
> Right click on it and use "Save Link As" to save it to your drive somewhere.

Since it has the agreement that you have to accept before you can download it I suspect it may not work as a direct download from a terminal.

But here is the link to the download you can just right click on it and do the same thing so replacing the info in the commands you were using with the right link info should work just as well. [http://download.lightscribe.com/ls/lightscribe-1.18.1.1-linux-2.6-intel.deb](http://download.lightscribe.com/ls/lightscribe-1.18.1.1-linux-2.6-intel.deb)

That was it!  The system software was succesfully installed..

Thanks for all the help!  I knew it had to something simple I was doing wrong.

---

### Post by 2hot6ft2 on 2009-02-14
> **cptrohn said:**
> When I click the download file it tries to open with the deb installer.
That's because that's the action you have the browser set to. You could have it ask you what to do or save it somewhere automatically, or like you have it now to automatically open with an app.

In Firefox
Edit>Preferences>Main tab
second setting area down is "Downloads"
set it to what you want it to do.

---

