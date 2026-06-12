---
title: "Not root file system is defined edit from partition menu?"
date: 2011-03-08
forum: New to Ubuntu
---

### Post by trebornikrep on 2011-03-08
Hi 

I am getting this message which I see has been mentioned elsewhere. 

                                  [B]Re:' No root file system is defined edit from partition menu. '

 A solution given was[/B]             
                                                                You will probably wish to format the drive to ext3 or ext4. Then ensure that the drive is set as "/".
  
What on earth does that mean. I have Vista installed and want to run Ubuntu with windows. Does it matter how many drives I have? OK I am confused now. Any help gratefully accepted and please go easy on the technical terms.

Thanks

---

### Post by mcduck on 2011-03-08
Sounds like you are using the manual partitioning  option?

When you are configuring the partitions in the Ubuntu installer there's a field that allows you to set a mount point for a partition, and also another one to set the file system.

You need to have one partition with mount point set as "/" (this will be your main Linux partition) and file system set to any Linux file system (I recommend Ext4). And then you should have another smaller partition with mount point and file system both set to "swap" (this will be the equivalent of paging file in Windows).

---

### Post by trebornikrep on 2011-03-08
Thank you Mcduck. How do you configure the partitions in the Ubuntu installer? I just followed the instructions from the download. I am out of my depth I think. I need a step by step to follow please.

---

### Post by mcduck on 2011-03-08
select a partition and click the "Change" button in the partitioning window.

edit: I tried to find a decent step-by-step guide for you, I suppose this is as close as you can get: [http://news.softpedia.com/news/Installing-Ubuntu-10-10-160966.shtml]("http://news.softpedia.com/news/Installing-Ubuntu-10-10-160966.shtml")

---

### Post by MrPok on 2011-03-08
Hi trebornikrep,

I don't know your computer skills, so don't feel offended if the stuff below is *too easy*. (Also, this isn't *exactly* how things are, but it will help you understand ;))

It does not matter how many drives you have, you will always be able to have *both* Windows and Ubuntu (or any other operating system) on your computer. 
(For example, I used to have only 1 drive in my computer, but I had both Windows and Linux installed on it.) 
The way to have this is to divide your drive in a part for Windows and a part for Ubuntu -- we call these "partitions".

An operating system, like Windows or Ubuntu, needs to store all its files somewhere and be able to retrieve them. It uses a "file system" to accomplish this. 
There are many different types of file systems, but the ones worth remembering are those used with Windows (namely *FAT* and *NTFS*) and some used with for example Ubuntu (namely *ext3* and *ext4*).
(For example, my home computer Windows 7 uses the *NTFS* filesystem, and Ubuntu uses *ext4*)

As in Windows, you can represent your file system in a tree-like structure, just like in "My Computer". The "root" of the tree is in most Windows for example **C:\** (You'll notice this if you open your "My Computer" in Windows) In that root, there are some directories (or "folders) and some files etc.
In Ubuntu (and other Linux'es), instead of using the symbol "**\**" for the root folder, we use the "**/**" symbol.

When people say:
> ..ensure that the drive is set as "/".they mean that the filesystem (*ext3* or *ext4*, depending on your choice) should know that it is supposed to store the root folder (with other folders and files) on that particular drive.

Ok, enough with the background information: I see you are already getting some more help.

Good Luck!

Kind regards,
Paul

---

### Post by trebornikrep on 2011-03-08
Select a partition. OK  Where am I looking exactly, on my computer C drive. Sorry to be so thick but where are these partitions, Where am I working exactly

Bob

---

### Post by trebornikrep on 2011-03-08
Oh now I see for advanced users only, not me then. I will carry on just using the CD I think, far too risky for me. I suppose I could erase disc after backing up programs etc, I can't see me using windows much. Good idea?

Thanks 

Bob

---

### Post by trebornikrep on 2011-03-08
Yes thanks Paul,as I've said elsewhere a bit complicated for me I will stick with the CD trial.

Thanks

Bob

---

### Post by MrPok on 2011-03-08
> **trebornikrep said:**
> Yes thanks Paul,as I've said elsewhere a bit complicated for me I will stick with the CD trial.
That won't get you the full Ubuntu experience in terms of functionality and performance etc. ;) I understand your concerns though. 

Backing up your *documents* is always a good thing to do. Do understand though, that backing up *programs* is a *different thing*. Most of the time you won't be able to backup the program itself, only the documents produced by it.

Say you would still like to have both Windows Visa and Ubuntu 10.10 on your computer, and you want to choose which on to start after you've turned on you computer:
google a bit for 
"Ubuntu Windows dual boot how" ,or
"Ubuntu Windows dual boot how resize partition"

That will give you enough tutorials on how to do this easily. Just remember that many many many people have done the exact same thing before you did, so after a bit of googling you will most likely end up with a good howto. :)

That said, wiping the drive won't be necessary as long there is enough space for Ubuntu "to live on".. ;)

Good luck!

---

### Post by trebornikrep on 2011-03-08
Thanks Paul I have got the page mentioned by Mcduck earlier in the thread. I am keen to learn and will have a go when I've got plenty of time.

Bob

---

### Post by mcduck on 2011-03-08
> **trebornikrep said:**
> Select a partition. OK  Where am I looking exactly, on my computer C drive. Sorry to be so thick but where are these partitions, Where am I working exactly

Bob

In the Ubuntu's installer, after you have started the computer with the Ubuntu CD and launched the installer.

Right in the stage where you got the "no root file system defined" error you mentioned in your first post.

---

### Post by trebornikrep on 2011-03-08
I installed directly from the home page so I did not have this option. when I installed with the CD for a try out it just gave me the erased option followed by the advanced users partition. I need to study this more. I just wonder if I really need windows at all which would make the whole process easier?

Thanks for your help
Bob

---

### Post by mcduck on 2011-03-08
> **trebornikrep said:**
> I installed directly from the home page so I did not have this option. when I installed with the CD for a try out it just gave me the erased option followed by the advanced users partition. I need to study this more. I just wonder if I really need windows at all which would make the whole process easier?

Thanks for your help
Bob

Directly from the home page? I assume you mean you used the Wubi installer inside Windows?

I don't think it even has such partitioning options, can't really say. Anyway, if that's what you've been doing then ignore the guide I posted, that's only for a real standalone install instead of installing inside Windows.

Anyway, the manual partitioning really isn't that hard, at least as long as you follow a guide and have a grasp of the basic idea of a [partition]("http://en.wikipedia.org/wiki/Disk_partitioning")

edit: Just letting the installer get rid of the Windows would of course be really easy, as that would allow it to do everything automatically for you, but you might want to run Ubuntu for a while alongside Windows (or at least from a Live CD) to find out if it does everything you want to do and if you'd feel comfortable running it as your only operating system. Especially if you don't have a recovery CD for your Windows setup, as manual installation of Windows (including all the required drivers & additional software) from a normal Windows CD is quite a lot harder than getting Ubuntu to work is... :D

---

### Post by trebornikrep on 2011-03-08
Yes the Wubi installer is there. It seems you can get all the plugins for everything so I'll just experiment with the CD for a while.

Bob

---

### Post by grthinker on 2011-07-21
I've got the same problem trying to install 10.04.2 LTS so that I can do WITHOUT 11;04 (which I really think a downgrade) as long as possible. Anyway, what does partition page look like after setting the partitions, and how large should the partitions be? Would it be possible to send an actual PICTURE of what it should look like? :confused:

---

### Post by oldfred on 2011-07-22
@grthinker
Welcome to the forums, but it would be better to start your own thread.

A few links to get you started, Herman are very detailed:
Ubuntu Install steps - then choose guide, close to what you want.
[http://members.iinet.net/~herman546/index.html]("http://members.iinet.net/%7Eherman546/index.html")
Installs with good screenshots/examples:
[http://members.iinet.net.au/~herman546/p22.html]("http://members.iinet.net.au/%7Eherman546/p22.html")
Install with separate /home from aysiu
[http://www.psychocats.net/ubuntu/installseparatehome](http://www.psychocats.net/ubuntu/installseparatehome)

The Hedge show graphically how to delete & create partitions:
[http://ubuntuforums.org/showthread.php?t=1713649](http://ubuntuforums.org/showthread.php?t=1713649)

---

