---
title: "How to open .pptx format"
date: 2008-12-07
forum: New to Ubuntu
---

### Post by banerjeerupak on 2008-12-07
I am using Ubuntu 8.10
I have received an email with a presentation in the .pptx format supported by Microsoft Office 2007. How do i open it. Openoffice does not support the format. 

Please help

---

### Post by lovelyvik293 on 2008-12-07
Hai man you can use the abiword version 2.6.5 or later it works witht the office 2007.

---

### Post by banerjeerupak on 2008-12-07
Is this some kind of a software.

Or just an update for the openoffice??

---

### Post by gjoellee on 2008-12-07
> **banerjeerupak said:**
> Is this some kind of a software.

Or just an update for the openoffice??

click on the link below:
[apt://abiword](apt://abiword)

(you might have to wait up to 30seconds)

click on install and then Abiword will download and install automatically. 

if this link does not work, copy and paste the following command:
```
sudo apt-get update && sudo apt-get install abiword
```if you get a question to either press "N" or "Y" hit Y


remember to press the enter-button when after something you have written.

---

### Post by lovelyvik293 on 2008-12-07
It's a software.

---

### Post by Bölvaður on 2008-12-07
> **lovelyvik293 said:**
> Hai man you can use the abiword version 2.6.5 or later it works witht the office 2007.

Abiword is documents only. I thought Presentation had some sort of pptx support. Find Presentation (Applications &#8594; Office &#8594; Presentation) and open the file from there (file &#8594; open).

You might need to get ooo3

I'll add how

please do not listen to the people above me, they are not solving your problem, unless if I very badly misunderstood everything.

---

### Post by banerjeerupak on 2008-12-07
Ok found it.
But should i get the one from Ubuntu repository or from the site only

---

### Post by lovelyvik293 on 2008-12-07
@Bölvaður sorry for my mastake.Abiword only works with the docs.

---

### Post by Bölvaður on 2008-12-07
> **banerjeerupak said:**
> Ok found it.
But should i get the one from Ubuntu repository or from the site only

Add this via software sources

```
deb http://ppa.launchpad.net/openoffice-pkgs/ubuntu intrepid main
```

you probably are using ubuntu  intrepid (8.10)

if you are not then you can change the text like this:

```
deb http://ppa.launchpad.net/openoffice-pkgs/ubuntu jaunty main
```

---

### Post by Bölvaður on 2008-12-07
> **lovelyvik293 said:**
> @Bölvaður sorry for my mastake.Abiword only works with the docs.

There is a light weight presentation application similar to how abiword is, but I think open office 3 is the way to go.

My brother managed to open pptx files on ooo2 though, dunno how.

---

### Post by AndyCooll on 2008-12-07
> **Bölvaður said:**
> Abiword is documents only. I thought Presentation had some sort of pptx support. Find Presentation (Applications &#8594; Office &#8594; Presentation) and open the file from there (file &#8594; open).

You might need to get ooo3

I'll add how

please do not listen to the people above me, they are not solving your problem, unless if I very badly misunderstood everything.
As the above post says. To make things clear, Abiword will **not** open .pptx files.

What you need is OpenOffice 3.0. (i.e. the one after the version that comes with Intrepid). There's a thread on these forums which shows you how to download and install it.

:cool:

---

### Post by banerjeerupak on 2008-12-07
It is true that presentation is getting opened from the presentation viewer of openoffice. 

however, the formatting error is coming and a lot of colours are not coming as was originally presented. 

Please let me know what to do.

---

### Post by banerjeerupak on 2008-12-07
Downloading Openoffice 3.
will install it and check.
thanks for all the help guys

is installation of openoffice 3 very different??

---

### Post by Bölvaður on 2008-12-07
> **banerjeerupak said:**
> It is true that presentation is getting opened from the presentation viewer of openoffice. 

however, the formatting error is coming and a lot of colours are not coming as was originally presented. 

Please let me know what to do.

Did you add the line I suggested to your software sources (it will automatically install open office 3 on  your computer)?

Open office 3 has much better support for mso2007 (no thanks to ms for not giving up the file format).


What I would do if I had ooo2 and opening .pptx files fails.

1. install open office 3.

if that fails

2. try see the content through text editor or firefox or something

and then:

3. complain to the guy that sent me the file and ask for .ppt file format, or odp.

4. ask that guy to keep sending you files that you are able to open, buy me mso2007 or use google docs

---

### Post by Bölvaður on 2008-12-07
> **banerjeerupak said:**
> Downloading Openoffice 3.
will install it and check.
thanks for all the help guys

is installation of openoffice 3 very different??

if you got the .deb file then it shouldn't be too much fuss, but I would rather have you doing like I first said in this thread:

Put this in your Software Sources

deb [http://ppa.launchpad.net/openoffice-pkgs/ubuntu](http://ppa.launchpad.net/openoffice-pkgs/ubuntu) intrepid main



System &#8594; Administrator &#8594; Software Sources
&#8594; Third-Party Software
+ Add...
(copy and paste:)
deb [http://ppa.launchpad.net/openoffice-pkgs/ubuntu](http://ppa.launchpad.net/openoffice-pkgs/ubuntu) intrepid main

---

### Post by banerjeerupak on 2008-12-07
well i have downloaded the .tar.gz file. 

how do i proceed now??

---

### Post by nvikram on 2008-12-07
I have many cases where I would like to convert Microsoft PowerPoint 2007 to .odp or regular .ppt. What I find the easiest, is [http://zamzar.com](http://zamzar.com). You just follow the steps at the bottom of the page and it will automatically email you your new file. Hope this helps!

---

### Post by snova on 2008-12-07
> well i have downloaded the .tar.gz file. 

how do i proceed now??

With difficulty, trying it this way. You're much better off following the instructions to add a repository.

Rephrased:

[LIST=1]
[*] Open Synaptic
[*] Settings -> Repositories
[*] Third Party Software
[*] Add
[*] Copy this: "deb [http://ppa.launchpad.net/openoffice-pkgs/ubuntu](http://ppa.launchpad.net/openoffice-pkgs/ubuntu) intrepid main"
[*] Add source
[*] Reload (toolbar on top)
[*] Find and install OpenOffice 3 (I don't know the precise package name).
[/LIST]

That should do it, I hope.

---

### Post by chrisod on 2008-12-07
If you are still having problems you can ask the person that sent you the presentation to save it as a .ppt file and then OO will definately open it just fine.

---

### Post by halitech on 2008-12-07
> **nvikram said:**
> I have many cases where I would like to convert Microsoft PowerPoint 2007 to .odp or regular .ppt. What I find the easiest, is [http://zamzar.com](http://zamzar.com). You just follow the steps at the bottom of the page and it will automatically email you your new file. Hope this helps!

+1 on zamzar.com, I used it just last week to convert a docx that someone sent me. sent them the file, went to get a sandwich, came back and I had the converted doc file. Only downside is the 100meg limit for free conversions.

---

### Post by manasmohan on 2008-12-08
i have added the new entry in the software sources but have not got the open office in the add or remove window....

---

### Post by banerjeerupak on 2008-12-08
well i have added it to the software sources. I'll proceed now.

.tar.gz option was really unadvisable. I agree now.

I'll try the zamzar.com and see what benefits i can get for the time being

---

### Post by banerjeerupak on 2008-12-08
Adding that link to the repositories list did not help. It still only downloaded OpenOffice 2.4

---

### Post by chrisod on 2008-12-08
Did you reload the repository indexes after adding it?

---

### Post by acreech on 2008-12-08
> **banerjeerupak said:**
> Adding that link to the repositories list did not help. It still only downloaded OpenOffice 2.4

I added that to the repository and I have the same issue that it won't upgrade my OpenOffice 2.4 to Open Office 3.0

---

### Post by Spitz on 2008-12-08
Same here, I have added the repository, but can not find any open office 3 packages, and nothing happens if I try to update.

I would love to be able to open those x-documents!

---

### Post by hobo89 on 2008-12-08
I have also added the source to the repositories, reloaded the indexed and searched through looking for OpenOffice.org 3 (I have no real need for it but saw people were having problems so thought I'd give it a shot myself to see if I could help). It seems everything refers to 2.4.

A quick google search for how to install 3 on 8.10 (and 9.04) shows that the packages for these versions of Ubuntu have been removed, it cannot be installed from the repositories.

Searching these forums I found this post, seems to be the easiest follow.
[http://ubuntuforums.org/showpost.php?p=6172120&postcount=9](http://ubuntuforums.org/showpost.php?p=6172120&postcount=9)
Edit: You need to cd to the directory you downloaded the tar.gz to before unpacking, in case anyone doesn't figure that themselves (i.e. me on the first attempt to unpack).

---

### Post by Spitz on 2008-12-08
Thanks, but I think I will wait until they add it somewhere again, since I like to let the update manager take care of updates. (or do the applications that you download and install separately update them selves to?)

---

### Post by hobo89 on 2008-12-08
> **Spitz said:**
> Thanks, but I think I will wait until they add it somewhere again, since I like to let the update manager take care of updates. (or do the applications that you download and install separately update them selves to?)

I believe you would have to add the new source to the repositories in order for it to update via the update manager. Hopefully installing it this way and adding the source at a later date will update the existing installation, can anyone confirm this? Or will it install another copy from the repositories alongside this install?

---

### Post by hobo89 on 2008-12-09
OpenOffice 3 is now back in the repositories (typical after I installed from source last night). So to install:

Remove 2.4:
```
sudo apt-get remove $(dpkg -l |grep ^ii|grep openoffice|cut -f3 -d' ')
```

Add the repository:
System > Administration > Synaptic Package Manage > Settings > Repositories > Third Party Software > Add > "deb http://ppa.launchpad.net/openoffice-pkgs/ubuntu" (copy and paste without quotes into the "APT line" box)
Click Close, message box will come up saying something about needing to reload packages, close the message box and click Reload in the top left corner of Synaptic.

Install:
Type in the Quick search box "openoffice", you should now see "openoffice.org" in the list with Latest Version "1:3.0.0-6ubuntu0intrepid1", select the checkbox and "Mark for Installation" It will list other changes it needs to make, such as installing other packages. Click Apply at the top, and confirm any message boxes that pop up and leave it to do it's thing.

You should now have OpenOffice.org 3.0 installed. If, in the menu, clicking the launchers does not work, log out and log back in again and it should be fine.

Hope this helps.

---

