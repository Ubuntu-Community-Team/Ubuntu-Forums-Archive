---
title: "Installing Songbird"
date: 2010-01-09
forum: New to Ubuntu
---

### Post by iggy pop on 2010-01-09
Have almost got Ubuntu the way i want except i would like to install Songbird. As i couldn't find Songbird in Synaptic i went here: [http://www.songbirdnest.com/](http://www.songbirdnest.com/) and downloaded it to my desktop. I then found a tutorial covering how to install Songbird here: [http://snipurl.com/u0xtq](http://snipurl.com/u0xtq)

So i did as instructed and downloaded the latest version opened a terminal and typed:
sudo tar -xvzf Songbird*.tar.gz -C /opt/ and got the following output:

iggy pop@iggy pop-dektop: ~$ sudo tar -xvzf Songbird*.tar.gz -C /opt/
[sudo] password for iggy pop:
tar: Songbird*.tar.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Exiting with failure status due to previous errors
iggy pop@iggy pop-desktop: ~$

Could someone help me please.

---

### Post by pararoly on 2010-01-09
Hi IggyPop,

Does the following get you any further....?

sudo tar -xvzf /home/YOUR-USER-NAME/Desktop/Songbird*.tar.gz -C /opt/

Good luck
Best wishes
Roland

---

### Post by Dayofswords on 2010-01-09
you can read this to find a deb
[https://help.ubuntu.com/community/Songbird#Installing%20Songbird%20with%20a%20.deb](https://help.ubuntu.com/community/Songbird#Installing%20Songbird%20with%20a%20.deb)

---

### Post by iggy pop on 2010-01-09
That certainly did the trick pararoly and thanks

But after following the rest of the tutorial and even getting Songbird's image to appear on the desktop i was disappointed to find that when i did click on the Songbird image i got the following error:

There was an error launching the application
Details: Failed to execute child process "songbird"
(No such file or directory)

---

### Post by iggy pop on 2010-01-09
Just looked under Applications -> Sound & Video and there's no mention of Songbird?
But if i navigate to /opt/Songbird i can start the program from there?

---

### Post by HomoGleek on 2010-01-09
> **Dayofswords said:**
> you can read this to find a deb
[https://help.ubuntu.com/community/Songbird#Installing%20Songbird%20with%20a%20.deb](https://help.ubuntu.com/community/Songbird#Installing%20Songbird%20with%20a%20.deb)
Id echo this as the best option for you :)

---

### Post by waspbr on 2010-01-09
The easiest way to install songbird AFAIK is through getdeb.net. 

you can just go to  [http://www.getdeb.net]("http://www.getdeb.net"), from there you go to the apps tab and search for songbird. 

once you find it you can follow its instructions, which simply boil down to installing this package, [click here to install the package]("http://archive.getdeb.net/install_deb/getdeb-repository_0.1-1~getdeb1_all.deb") and then once you have installed he getdeb package just click on the install button on the getdeb page.

---

### Post by iggy pop on 2010-01-09
I'm lost!

I have installed the getdeb package and located Songbird 1.4.3-1 ~getdeb1
But when i click on "install this now" the "Launch Application" window opens up with two options.

I selected the "aprurl" option and then clicked on "OK" but nothing happens?

I know this is stupid but could someone please point out where or what i am doing wrong please.

---

### Post by HomoGleek on 2010-01-09
> **iggy pop said:**
> I'm lost!

I have installed the getdeb package and located Songbird 1.4.3-1 ~getdeb1
But when i click on "install this now" the "Launch Application" window opens up with two options.

I selected the "aprurl" option and then clicked on "OK" but nothing happens?

I know this is stupid but could someone please point out where or what i am doing wrong please.
[http://www.getdeb.net/updates/Ubuntu/all#how_to_install](http://www.getdeb.net/updates/Ubuntu/all#how_to_install)

All instructions are in there

---

### Post by walkingbeard on 2010-02-21
Cheers guys, very useful.  Why can you not get it from the Ubuntu reps any more though?

---

### Post by sandyd on 2010-02-21
> **walkingbeard said:**
> Cheers guys, very useful.  Why can you not get it from the Ubuntu reps any more though?

1. Ill probably be placed in universe, so MOTU deals w/ that
2. Many applications are not in the repos cause that would overload the packagers/maintainers/QC.
3. Which is why PPAS exist. So that people who dont want to become part of MOTU due to all the work can still package stuff.

---

### Post by peace.gangsta on 2010-03-05
I am reinstalling Songbird.Downloaded package,Extracted it to /opt/Songbird.
I was creating a Shortcut in the main menu/Sound & Video.Now I was browsing for icons but it seems like menu no longer supports .png files.It took me to a  /usr/share/icons/hicolor/scalable/apps . This folder had a number of .svgs.
This means I need a songbird.svg file.I could not find it.
Help!

---

