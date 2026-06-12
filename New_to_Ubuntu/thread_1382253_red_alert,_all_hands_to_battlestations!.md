---
title: "red alert, all hands to battlestations!"
date: 2010-01-15
forum: New to Ubuntu
---

### Post by vnpifhf on 2010-01-15
right i have a problem,

i have downloaded the latest wine as i cant open any windows filw from my current wine
i have ubuntu 9.10, i downloaded the latest one via the link highlighted from the picture below
[IMG]http://i892.photobucket.com/albums/ac121/jahangir99/Screenshot-2.png

i downloaded it and i have a load of meaningless files that i have no idea what to do with them?! or how to open them and install wine and i cant find it in FAQ
pic below
[IMG]http://i892.photobucket.com/albums/ac121/jahangir99/Screenshot-1-1.png

and also i have another problem.
can someone give me a very basic beginners guide of wine as i still dont understand it fully, i have partitioned hard drive,, i C and a D, i can still access my C drive on ubuntu and it has my microsoft office key e.t.c and i cant open it (maybe the problem is its on the windows hard drive) and if i get micro office somewhere from the web i wont have they key and ive already used it three times) so is that a problem? 
and how do i get all the stuff into my ubuntu drive, all my apps e.t.c
do i just copy the program file folder and paste it into my ubuntu partition??
so i can run wine then??
i recently tried to download windows live messenger but failed as i right clicked the installer to run it with wine but it did not work.


i really like ubuntu but i am struggling with some aspects of it, i.e opening windows files and using google chrome (but not being able to open it)
etcetera etcetera

lol

pc details i have windows vista with a ubuntu partition, 80 goes to vista and 80 to ubuntu
pentium dual core 2 gig ram (if u needed this info to sort my problem)

all help would be welcome as i am a noob in this area of expertise :) ;)

Thank you and God Bless.

---

### Post by alwayshere on 2010-01-15
see this it works [http://www.winehq.org/download/deb]("http://www.winehq.org/download/deb")

---

### Post by vnpifhf on 2010-01-15
i have downloaded the latest not the stable and need to compile em i think?

---

### Post by samigina on 2010-01-15
Look, you downloaded the source code, this means that you need to compile it. Wrong choice for a noob. The easiest way is to install the package for your distro (Ubuntu. The link that the Alwayshere gives to you is the right place to find it. Just read, there is the lates verison, just follow the instructions.

And please, dont say the information that Alwayshere gives you is irrevelant, you MUST to read before complain.

Let us know if you dont understand something and we will help you.

---

### Post by sliketymo on 2010-01-15
here is more info I found by following the link supplied to you earlier,

[http://wiki.winehq.org/](http://wiki.winehq.org/)

A little research goes a long way toward enabling one to use software that is new to one.Folks are just trying to help.If you don't want to follow-up on the help offered,that is up to you.

---

### Post by pricetech on 2010-01-15
Just a suggestion, but based upon your other posts, you might want to take the time to read a little more about the forums themselves, specifically the code of conduct, before you piss off everyone who is trying to help you.

Then come back and ask in a civil tone, adhering to the code, and you'll find the community to be quite helpful.

There, I said it.

---

### Post by realzippy on 2010-01-15
Is this correct:

You have wine installed and try to install a newer version of it because you can not access windows files from it?
Edit: lol

---

### Post by Cheesemill on 2010-01-15
Did you read my post in your previous thread about this?
[http://ubuntuforums.org/showpost.php?p=8670800&postcount=11](http://ubuntuforums.org/showpost.php?p=8670800&postcount=11)

Just follow the instructions [here]("http://www.winehq.org/download/deb") to install wine, then run the Office 2007 **installer**. Done.

You can't use wine to run programs that are already installed on a Windows drive, you have to install them again in Ubuntu.

---

### Post by Techsnap on 2010-01-15
> if you cant help me with my problem and the questions dont post at all because this was completely irrelevant to the questions

```
tar -xjvf wine-1.1.36.tar.bz2 && cd wine-1.1.36 && ./configure && make && sudo make install
```

Doesn't work? Find the build dependencies yourself, you asked for help with what you wanted so there I did. But with that attitude you can sort out all the build deps because Ubuntu doesn't include them by default, have fun.

---

### Post by JimInLakeland on 2010-01-15
Just go to the Ubuntu Software Center and install Wine from there. It will install all dependencies as well.

---

### Post by Techsnap on 2010-01-16
> Just go to the Ubuntu Software Center and install Wine from there. It will install all dependencies as well.

It's not the latest version that way.

---

### Post by vnpifhf on 2010-01-16
ok im real sorry, i am really frustrated with ubuntu but like it at the same time :/ , im a noob at this kinda soflware and also ive got a bad attitude i know and im sorry you lot who have tried to help, ;)

i have looked into the older posts and could not find this one

i got the office onw thanks

i have downloaded windows live messenger installer from the website

but cannot install it with wine :?
help!

and are these things right, u cannot run wine from programs already installed in ur windows partition and trying to boot em off linux with wine?

so all my old apps are gone i.e google chrome /bearshare e.t.c

---

### Post by Cheesemill on 2010-01-16
Search the Wine database to see which apps will run:
[http://appdb.winehq.org/](http://appdb.winehq.org/)

You should always try finding native Linux apps before trying wine, it should only be used as a last resort. There is a Linux version of Chrome, for instance.

---

### Post by vnpifhf on 2010-01-16
oh god your a lifesaver, Thanks!

now me problem with windows live messenger and how do i do that because i have tryed to downloaded it but failed

lol all help much appreciated

---

### Post by Roger Allott on 2010-01-16
> **jahangir99 said:**
> oh god your a lifesaver, Thanks!

now me problem with windows live messenger and how do i do that because i have tryed to downloaded it but failed

lol all help much appreciated

Install Pidgin (or Empathy) from Ubuntu Software Centre. Either is a pretty godd alternatie to MSN Messenger. You'll probably find that Empathy was installed automatically when you installed 9.10.

---

### Post by kenuf on 2010-01-16
Empathy supports the Live messenger very well, and it is already installed in Ubuntu (9.1)

Applications> Internet> Empathy IM Client
Select MSN for the account type and provide you Live Login info and my contacts appeared.

Windows and Linux are just two different things...  
You may need to stop thinking about the program names and start thinking about what they do.

Example:
OpenOffice Writer (already installed in Ubuntu) can do almost everything MS Word can, and doesn't require emulation.

---

### Post by ankspo71 on 2010-01-16
Hi,
'amsn' is available from the ubuntu repositories. It has the look and feel of msn messenger. You can find that in ubuntu software center and synaptic. I personally haven't tried it for very long, because I'm not much of a chatter.

If you are looking for something multi-protocol, then pidgin or empathy is probably what you would like better.

---

### Post by vnpifhf on 2010-01-16
right

i need wlm for video calling and voice calling

and also i cant see peoples names because they have windows live (name colour addon)

so the only suitable choice is windows live messenger

but how do i do it?

---

### Post by kenuf on 2010-01-16
I believe that video with MSN will be in the next major build.
I read that Empathy 'has the ability' but that it was disabled in this build because it wasn't quite ready for the 'end user'.
If you really depend on all of the Windows apps then you might think about Windows primary and running Ubuntu within, until you know how to make it really fit your needs.

---

### Post by ankspo71 on 2010-01-16
Will MSN Messenger 7.0 do the things you need it to do?
If it does, go here [http://www.microsoft.com/downloads/en/default.aspx](http://www.microsoft.com/downloads/en/default.aspx)
and search for and download "msn messenger 7.0"
The filename is Install_MSN_Messenger.exe

Once you have it downloaded, right click on it and select open with "wine windows program loader". Install as usual.

That's the latest version I can find that will install in wine.

I think the reason why the current LIVE version installers don't work are because they have to be authorised by microsoft, then the installers will download the necessary files. I can see an authorisation.xml file inside the exe.

Playonlinux has an 8.0 version but it is in french. 

Hope this helps some.

---

