---
title: "Where should I install Adobe Reader to?"
date: 2010-11-01
forum: New to Ubuntu
---

### Post by gabriella on 2010-11-01
Hello guys..

Yes a sill question but I need to know. 

I just downloaded Adobe Reader 9.4 for Linux. I clicked on the .tarbz2 file to extract it and of course I get the directory list to select where I should extract it to. Where should I extract/install it to? I know I could put it anywhere but to keep things tidy I'd like to put it alongside similar existing applications.

So where do you recommend I install it?

Thanks

---

### Post by mikewhatever on 2010-11-01
Just select 'Extract here'. Simply extracting will not install it, you'd have to run the installer afterwards.

---

### Post by Paul820 on 2010-11-01
Why not just enable **Canonical Partners** is synaptic and install it from there?

---

### Post by lhb1142 on 2010-11-01
> **gabriella said:**
> Hello guys..

Yes a sill question but I need to know. 

I just downloaded Adobe Reader 9.4 for Linux. I clicked on the .tarbz2 file to extract it and of course I get the directory list to select where I should extract it to. Where should I extract/install it to? I know I could put it anywhere but to keep things tidy I'd like to put it alongside similar existing applications.

So where do you recommend I install it?

Thanks

Dear Ms. Gabriella,

This is none of my business of course but I suggest that you forget about Adobe Reader, a big, bloated, 'full-of-holes' program in favor of the standard Document Reader already available in Ubuntu.

My wife and I formerly used Adobe Reader on our respective Ubuntu computers and we both hated it. Among other things, when it is updated, it takes 'forever' for the Update Manager to download and install it. We uninstalled it and now use the Document Reader.

Another option would be to use Okular which is also a much better program than Adobe Reader for Linux.

This is just my two cents and I know it does not answer your question but I do hope it gives you some food for thought.

Lawrence

---

### Post by gabriella on 2010-11-01
> **mikewhatever said:**
> Just select 'Extract here'. Simply extracting will not install it, you'd have to run the installer afterwards.

Thanks for the reply.

Well I extracted it and the Adobe folder now sits in my home folder.

What next? If I click on the install file nothing happens?
And I will still need to install it to somewhere right?

---

### Post by Paul820 on 2010-11-01
Go to System->Administration->Software Sources
Click on the **Other Software** tab
If the checkbox next to Canonical Partners (not the source code one) isn't ticked, click to tick it.
If the **Canonical Partners** isn't there, click the **add** button at the bottom, then enter this
> deb [http://archive.canonical.com/](http://archive.canonical.com/) maverick partner
Changing **maverick** to the distro you are using. Click close, then reload.
In the terminal
> sudo apt-get install acroread

---

### Post by gabriella on 2010-11-01
> **lhb1142 said:**
> Dear Ms. Gabriella,

This is none of my business of course but I suggest that you forget about Adobe Reader, a big, bloated, 'full-of-holes' program in favor of the standard Document Reader already available in Ubuntu.

My wife and I formerly used Adobe Reader on our respective Ubuntu computers and we both hated it. Among other things, when it is updated, it takes 'forever' for the Update Manager to download and install it. We uninstalled it and now use the Document Reader.

Another option would be to use Okular which is also a much better program than Adobe Reader for Linux.

This is just my two cents and I know it does not answer your question but I do hope it gives you some food for thought.

Lawrence

Hi there,

Thanks for the comments. Previously there were reasons why I needed Adobe alongside the default so I'd like to do it again, for now that is. However, you make some good points and I will put some thought into them!

G

---

### Post by mrnelson1986 on 2010-11-01
> **gabriella said:**
> Thanks for the reply.

Well I extracted it and the Adobe folder now sits in my home folder.

What next? If I click on the install file nothing happens?
And I will still need to install it to somewhere right?

right click the "install" file and make sure it has permission to be used as an executable, otherwise it will fail that file check and do nothing when you click on it...but like other people have said i recommend using a pdf viewer other than adobe reader

---

### Post by gabriella on 2010-11-01
> **Paul820 said:**
> Go to System->Administration->Software Sources
Click on the **Other Software** tab
If the checkbox next to Canonical Partners (not the source code one) isn't ticked, click to tick it.
If the **Canonical Partners** isn't there, click the **add** button at the bottom, then enter this

Changing **maverick** to the distro you are using. Click close, then reload.
In the terminal

OK thanks for that. Thats seems a more straightforward way of doing it. I always get a bit tangled up with the .tarbz thing!

---

### Post by edm1 on 2010-11-01
Yes adobe reader can be installed from the repository. Just to let you know the .tar.bz2 file you downloaded is the universal linux file and will require you to know how to compile software for yourself. In the future if you wish to install software thats not in the repository you should go for the .deb file as that is specific to debian (and so Ubuntu) and is installed by just clicking on file.

---

### Post by mikewhatever on 2010-11-01
> **gabriella said:**
> Thanks for the reply.

Well I extracted it and the Adobe folder now sits in my home folder.

What next? If I click on the install file nothing happens?
And I will still need to install it to somewhere right?

The 'INSTALL' file is an installation script you'll need to run.

cd AdobeReader

sudo ./INSTALL

PS: There is a debian package available from Adobe.com that will get installed by double clicking. Adobe Reader is also available through Canonical's partner repository. Try those if you have trouble with the CLI.

---

### Post by gabriella on 2010-11-01
OK some good points made by all on this subject!

My final question then is.....

When I downloaded the .tarbz it opened with Archive Manager and I followed instructions, i.e. "Run" "extract" etc. Where is the file I downloaded located? I'm confused. I'd like to delete it now I have better sugestions rather than sitting junking things up. 

I already deleted the folder I extracted to my Home directory

Thanks

---

### Post by Paul820 on 2010-11-01
All files downloaded from the internet should go into your **Downloads** folder inside your home directory.

---

### Post by mikewhatever on 2010-11-01
> **gabriella said:**
> OK some good points made by all on this subject!

My final question then is.....

When I downloaded the .tarbz it opened with Archive Manager and I followed instructions, i.e. "Run" "extract" etc. Where is the file I downloaded located? I'm confused. I'd like to delete it now I have better sugestions rather than sitting junking things up. 

I already deleted the folder I extracted to my Home directory

Thanks

It's probably in the /tmp folder. Deleting it manually is unnecessary, as it will get autodeleted either when Firefox is closed or on reboot.

---

### Post by gabriella on 2010-11-01
Thanks everyone.
I've got it all sorted now!:)

---

