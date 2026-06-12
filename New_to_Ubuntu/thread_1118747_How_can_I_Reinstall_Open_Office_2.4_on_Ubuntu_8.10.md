---
title: "How can I Reinstall Open Office 2.4 on Ubuntu 8.10"
date: 2009-04-07
forum: New to Ubuntu
---

### Post by dbuss63 on 2009-04-07
I attempted to install OpenOffice 3.0 using the procedure found on Softpedia.com.  Unfortunately, the installation was incomplete.  When I open OpenOffice 3.0 there is no text in the menu bar.  I would like to reinstall the earlier version of Open Office 2.4 on Ubuntu 8.10.  Can anyone take me through the steps to accomplish this?  Thanks,
Dennis

---

### Post by LowSky on 2009-04-07
remove the openoffice repos you added, if those are the instructions you followed.

then go into synaptic, and remove openoffice and reinstall

---

### Post by dbuss63 on 2009-04-07
LowSky and Gambitt,
I tried both approaches with no luck.  I did download and unzipped the OpenOffice 2.4 files but I do not know where to put them or how to get Synaptic file manager to recognize them.  The only OpenOffice files on Synaptic file manager are for the 3.0 version.

This is one aspect of Ubuntu that has me completely confused.  If one downloads an application, why can't Synaptic file manager find the application and install it?  If one wants to uninstall an application, why isn't this straight forward?  From the absolute beginner's perspective, I'm afraid Windows has Ubuntu beat when it comes to installing and uninstalling software!
Dennis

---

### Post by Ms_Angel_D on 2009-04-07
> **dbuss63 said:**
> LowSky and Gambitt,
I tried both approaches with no luck.  I did download and unzipped the OpenOffice 2.4 files but I do not know where to put them or how to get Synaptic file manager to recognize them.  The only OpenOffice files on Synaptic file manager are for the 3.0 version.

This is one aspect of Ubuntu that has me completely confused.  If one downloads an application, why can't Synaptic file manager find the application and install it?  If one wants to uninstall an application, why isn't this straight forward?  From the absolute beginner's perspective, I'm afraid Windows has Ubuntu beat when it comes to installing and uninstalling software!
Dennis

Synaptics job is to download software from a repository and install it as well as updating any software that is listed in the repositories you tell it to monitor. So if  you download something outside of it synaptic doesn't know it exists.

Open Synaptic and search for OpenOffice.org make sure you mark anything you want to remove for complete removal if your nervous about removing a package ask before applying.

---

### Post by fballem on 2009-04-07
> **dbuss63 said:**
> LowSky and Gambitt,
I tried both approaches with no luck.  I did download and unzipped the OpenOffice 2.4 files but I do not know where to put them or how to get Synaptic file manager to recognize them.  The only OpenOffice files on Synaptic file manager are for the 3.0 version.

This is one aspect of Ubuntu that has me completely confused.  If one downloads an application, why can't Synaptic file manager find the application and install it?  If one wants to uninstall an application, why isn't this straight forward?  From the absolute beginner's perspective, I'm afraid Windows has Ubuntu beat when it comes to installing and uninstalling software!
Dennis

Forgive my lack of understanding. Am I correct that you downloaded a .deb file from softpedia.org and installed that file by double-clicking on the file?

If that's the case, then Open Office has probably been installed in Opt. You may confirm that by opening Nautilus (select Places from the menu on the top panel, then select File System from the left panel). I've attached three screenshots that should walk you through this.

In my case, I only have LightScribe, but you probably have Open Office installed there.

If you could also open your Software Sources (System > Administration > Software Sources). Please select the Third-Party tab and take a screenshot. This will let us know if you have enabled a PPA that may include Open Office 3.0.

Once we know this, then we may be able to help you further.

Thanks,

---

### Post by cbtengr on 2009-04-07
> **dbuss63 said:**
> LowSky and Gambitt,
I tried both approaches with no luck.  I did download and unzipped the OpenOffice 2.4 files but I do not know where to put them or how to get Synaptic file manager to recognize them.  The only OpenOffice files on Synaptic file manager are for the 3.0 version.

This is one aspect of Ubuntu that has me completely confused.  If one downloads an application, why can't Synaptic file manager find the application and install it?  If one wants to uninstall an application, why isn't this straight forward?  From the absolute beginner's perspective, I'm afraid Windows has Ubuntu beat when it comes to installing and uninstalling software!
Dennis

I installed OpenOffice 3.0 using the process described here:

[http://news.softpedia.com/news/How-To-Install-OpenOffice-org-3-0-in-Ubuntu-8-10-96449.shtml](http://news.softpedia.com/news/How-To-Install-OpenOffice-org-3-0-in-Ubuntu-8-10-96449.shtml)

This adds OpenOffice 3.0 to your repositories and allows installing from
Synaptic.  It's a 2 step process - add the source and the key.

If done this way, there is no need to download and install manually and the software will also be updated as needed.

---

### Post by dbuss63 on 2009-04-07
Thanks for your message.  I opened Opt from Nautilus but the folder containing the Open Office 2.4 installation files was not there.  The Open Office 2.4 files are now on my Desktop.  However, I cannot move them to Opt - I get an error message saying I can't move them to Opt.  The folder is called /home/dennis/Desktop/OOH680_m18_native_packed-1_en-US.9364

---

### Post by dbuss63 on 2009-04-07
Thanks for your message Cbtengr.  That's exactly what I did, however, the installation was not complete.  When I open Open Office 3.0, the menu bars have no text.  I tried several times to install it using the softpedia instructions but I get the same result.
Dennis

---

### Post by dbuss63 on 2009-04-07
> **fballem said:**
> Forgive my lack of understanding. Am I correct that you downloaded a .deb file from softpedia.org and installed that file by double-clicking on the file?

If that's the case, then Open Office has probably been installed in Opt. You may confirm that by opening Nautilus (select Places from the menu on the top panel, then select File System from the left panel). I've attached three screenshots that should walk you through this.

In my case, I only have LightScribe, but you probably have Open Office installed there.

If you could also open your Software Sources (System > Administration > Software Sources). Please select the Third-Party tab and take a screenshot. This will let us know if you have enabled a PPA that may include Open Office 3.0.

Once we know this, then we may be able to help you further.

Thanks,

fballem, thanks again.  Here is the screen shot:

---

### Post by fballem on 2009-04-07
Before you start, if the problem is that the text is not being displayed with the icons in the toolbar, then I believe that is by design (takes up room). If you hover over an icon in the toolbar, then the text will show for that icon. You can change the setting for how long this is displayed.

When you work with a product, you will get used to identifying the icons by sight. I'm sorry that I don't remember if text was displayed with icons in 2.4.

If you still want to go back to OpenOffice 2.4, then the following step by step instructions should do the job.

The screen shot wasn't totally clear, but I think that I see part of the problem - you have checked the PPA sites for Open Office 3.0.


Please try the following:

**Uninstall OpenOffice 3.0**

1/ Open Synaptic (System > Administration > Synaptic Package Manager)
2/ Search for OpenOffice - it should list the version 3.0.
3/ If the checkbox for OpenOffice.org is checked, then please right-click and select the option that says 'Mark for Complete Removal'. If the checkbox for OpenOffice.org is not checked, then right-click on each of the open office programs (OpenOffice.org-writer, OpenOffice.org-calc, OpenOffice.org-impress, and OpenOffice.org-base) and mark them for complete removal.
4/ Select Apply.
5/ Close Synaptic when the programs are removed.

**Remove local settings**

6/ Open Nautilus (Places > Home Folder)
7/ Press Ctrl-H. This will reveal the 'hidden folders'.
8/ Locate the folder labelled .openoffice.org This folder contains the settings for OpenOffice.
9/ Right-click on this folder and Move to Trash (or delete it). The settings between 3.0 (that you currently have) and 2.4 (the one that you want) are different.

**Adjust Source Settings**
10/ Open your Source List (System > Administration > Sofware Sources).
11/ Select the Third-Party Software tab.
12/ Uncheck any of the PPA sources that refers to Open Office.
13/ Select the Close button. You may get a warning that your software sources are out of date. Let the system update your packages.

**Install OpenOffice, which should be 2.4**

14/ Open Synaptic (System > Administration > Synaptic Package Manager).
15/ Search for Open Office.
16/ The version that is there should be version 2.4. I don't know if they have ported 3.0 to the backports for Intrepid. Mark the packages for installation that you want, and select apply.

**Do your local settings**

17/ Start up Open Office and do your settings.

Hope this helps.

---

### Post by dbuss63 on 2009-04-07
> **fballem said:**
> Before you start, if the problem is that the text is not being displayed with the icons in the toolbar, then I believe that is by design (takes up room). If you hover over an icon in the toolbar, then the text will show for that icon. You can change the setting for how long this is displayed.

When you work with a product, you will get used to identifying the icons by sight. I'm sorry that I don't remember if text was displayed with icons in 2.4.

If you still want to go back to OpenOffice 2.4, then the following step by step instructions should do the job.

The screen shot wasn't totally clear, but I think that I see part of the problem - you have checked the PPA sites for Open Office 3.0.


Please try the following:

**Uninstall OpenOffice 3.0**

1/ Open Synaptic (System > Administration > Synaptic Package Manager)
2/ Search for OpenOffice - it should list the version 3.0.
3/ If the checkbox for OpenOffice.org is checked, then please right-click and select the option that says 'Mark for Complete Removal'. If the checkbox for OpenOffice.org is not checked, then right-click on each of the open office programs (OpenOffice.org-writer, OpenOffice.org-calc, OpenOffice.org-impress, and OpenOffice.org-base) and mark them for complete removal.
4/ Select Apply.
5/ Close Synaptic when the programs are removed.

**Remove local settings**

6/ Open Nautilus (Places > Home Folder)
7/ Press Ctrl-H. This will reveal the 'hidden folders'.
8/ Locate the folder labelled .openoffice.org This folder contains the settings for OpenOffice.
9/ Right-click on this folder and Move to Trash (or delete it). The settings between 3.0 (that you currently have) and 2.4 (the one that you want) are different.

**Adjust Source Settings**
10/ Open your Source List (System > Administration > Sofware Sources).
11/ Select the Third-Party Software tab.
12/ Uncheck any of the PPA sources that refers to Open Office.
13/ Select the Close button. You may get a warning that your software sources are out of date. Let the system update your packages.

**Install OpenOffice, which should be 2.4**

14/ Open Synaptic (System > Administration > Synaptic Package Manager).
15/ Search for Open Office.
16/ The version that is there should be version 2.4. I don't know if they have ported 3.0 to the backports for Intrepid. Mark the packages for installation that you want, and select apply.

**Do your local settings**

17/ Start up Open Office and do your settings.

Hope this helps.

fballem,
Thanks for your suggestions.  I was able to uninstall OpenOffice 3.0 and reinstall the 2.4 version.  However, the same problem of no text on the tool bar reappeared on 2.4.  While adjusting the source settings after selecting the Third-Party Software tab and closing, I got an error message.  The screen shot is attached (sorry- it's a bit difficult to read).  I also have a screen shot of the OpenOffice Writer new file page.  As you can see there is no text on the upper screen bar nor is there text in the drop-down menus. I keep the cursor over the items on the tool bar but no text appears (the text was always present on my previous version).  If you have any more suggestions, I would appreciate hearing from you.
Dennis

---

### Post by perpetuo on 2009-04-07
i'm experiencing the same situation.
no text in the menu bars...

---

### Post by fballem on 2009-04-07
Could you please open Synaptic and do a search for language-pack. This should pull up a list of language packages contained in ubuntu. Please scroll through the list and identify which language packs are installed (the check box is filled in).

Thanks,

---

### Post by cbtengr on 2009-04-08
Did you "Import Key File" on the Authentication tab of the Software Sources window? 

[http://news.softpedia.com/news/How-To-Install-OpenOffice-org-3-0-in-Ubuntu-8-10-96449.shtml](http://news.softpedia.com/news/How-To-Install-OpenOffice-org-3-0-in-Ubuntu-8-10-96449.shtml) 

Right click HERE and "Save Link As..." the key file on your desktop. Go to the fourth tab, "Authentication", click the "Import Key File" button, navigate to the location were you've just saved the key file (File System/home/YOURUSERNAME/Desktop) and double click it. You will immediately see a new entry called "247D1CFF 2009-01-21 Launchpad PPA for OpenOffice.org Scribblers".

---

### Post by Jakey_TheSnake on 2009-04-08
Although I may be too late, you can install Open Office 3.0 by downloading it from the open office site, extracting it (to lets say your Desktop) then running:

```
cd ~/Desktop/OpenOfficedirectoryhere/

sudo dpkg -i *.deb
```

Then cd'ing to the menu integration folder and using the same install command.

---

### Post by fooman on 2009-04-08
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=109004&d=1239127036[/IMG]


are you using hardy or intrepid?  ...it looks like your using hardy,  but you apparently tried to install openoffice 3 using the intrepid repositories??

if you have not done so already,  go to software sources (system > administration > software sources) and *remove* each of 4 entries that you have for openoffice.  then close the software sources box.

if you have gone back to 2.4,  and want to try installing openoffice 3 again,  you might want to give [THIS]("http://ubuntuforums.org/showpost.php?p=6210799&postcount=1") guide a shot.  its pretty straightforward...*just make sure that you use the repository [COLOR=Red]for[/COLOR] [COLOR=Red]hardy[/COLOR]!!*

---

### Post by fballem on 2009-04-08
Good catch - thanks I missed that in my previous posts!

---

