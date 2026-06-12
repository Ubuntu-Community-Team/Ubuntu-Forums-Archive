---
title: "How can I unzip a tar.gz file?"
date: 2010-01-22
forum: New to Ubuntu
---

### Post by smdawson on 2010-01-22
I am trying to install code::blocks for my c++ class at school. The download file is as follows;

codeblocks_8.02-0ubuntu1.deb.tar.gz

Is there software I need to open this tar.gz file? If so, where can I get it and how can I open this file up?

---

### Post by Mornedhel on 2010-01-22
Just double click the archive.

---

### Post by Enigmapond on 2010-01-22
Yep, the stock Archive Manager should have no problem opening that...just double click or right-click->Extract

---

### Post by bodhi.zazen on 2010-01-22
> **smdawson said:**
> I am trying to install code::blocks for my c++ class at school. The download file is as follows;

codeblocks_8.02-0ubuntu1.deb.tar.gz

Is there software I need to open this tar.gz file? If so, where can I get it and how can I open this file up?

As you are taking a programming class, I suggest you look at bash and the man pages.

man tar

```
tar xzvf codeblocks_8.02-0ubuntu1.deb.tar.gz
```

---

### Post by Buuntu on 2010-01-22
> **bodhi.zazen said:**
> As you are taking a programming class, I suggest you look at bash and the man pages.

man tar

```
tar xvf codeblocks_8.02-0ubuntu1.deb.tar.gz
```

Well if it's also gzipped I believe you have to add a -z option as well

So it would look like:

```
tar -xvzf codeblocks_8.02-0ubuntu1.deb.tar.gz
```

Like everyone said though, man pages are life savers :).

---

### Post by smdawson on 2010-01-22
I see. I didn't realize that the archive manager was already opening the tar.gz file. Then I extracted all the files from there. 

Also, if I understand correctly, the code everyone posted is to open the tar, and tar.gz files from a terminal, right?

One more thing, when I was using the package installer it said a newer version is available and recomended finding it in the software channel. Where exactly can I find that? because obviously, a newer version sounds like brightest idea.

---

### Post by Mornedhel on 2010-01-22
Oh right, I never realized that, but Code::Blocks is packaged for Ubuntu and is available in the repositories.

Open the terminal and run

```
sudo apt-get install codeblocks
```

This will download, unpack, and install Code::Blocks for Ubuntu. If you need additional plugins, you can do

```
sudo apt-get install codeblocks-contrib
```

---

### Post by smdawson on 2010-01-22
ahhh. Thanks for the last bit of information Mornedhel.( that related to the Moredhel?) Is there a page on ubuntu that has the manual for codes and commands?

---

### Post by themusicalduck on 2010-01-22
Although that command can be used to install software from the repositories, the easiest way to find and install software is through the software centre - Applications > Ubuntu Software Centre

Or if you want to see every package available and which are installed on your system then go to System > Administration > Synaptic Package Manager.

---

### Post by bodhi.zazen on 2010-01-22
> **Buuntu said:**
> Well if it's also gzipped I believe you have to add a -z option as well

So it would look like:

```
tar -xvzf codeblocks_8.02-0ubuntu1.deb.tar.gz
```

Like everyone said though, man pages are life savers :).

Ooops, I will fix my post :redface:

---

### Post by thegreeneyes on 2010-08-24
Hi, I tried to install the newest version (10.05), but I do not find it in any repositories. following all the suggested procedures I only get version 8.02 to be installed.

Any suggestion about a repository I should include to get the latest version?

Thanks

---

### Post by Paul820 on 2010-08-24
First, remove codeblocks 8, open synaptic and search for codeblock and remove all that have a check next to it, then you need to add the wxwidgets source repos, open System->Administration->Software Sources, click on the 'other software' tab, click the 'add' button at the bottom. Now copy and paste this into it 
> deb [http://apt.wxwidgets.org/](http://apt.wxwidgets.org/) lucid-wx main

Now open a terminal and copy and paste this into it
> wget -q [http://apt.wxwidgets.org/key.asc](http://apt.wxwidgets.org/key.asc) -O- | sudo apt-key add -
sudo apt-get update
Now enter this in the terminal, just copy and paste
> sudo apt-get install libwxgtk2.8-0 libwxgtk2.8-dev wx2.8-headers wx-common
Now you need to get the binaries of codeblock 10.05, i don't know if you have them or not but just in case here is a link [http://www.codeblocks.org/downloads/26#linux]("http://www.codeblocks.org/downloads/26#linux")
Save to your home folder, right click and choose extract here. Open a terminal and cd to inside the folder, now enter this in the terminal
> sudo dpkg -i codeblocks_10.05-1_i386.deb codeblocks-common_10.05-1_all.deb libcodeblocks0_10.05-1_i386.deb codeblocks-contrib_10.05-1_i386.deb codeblocks-contrib-common_10.05-1_all.deb libwxsmithlib0_10.05-1_i386.deb codeblocks-doc-en_10.05-1_all.deb

If you are using the 64bit version, then change the **i386** to what it says on the deb, x86_64 or whatever.

That's it. :D

---

