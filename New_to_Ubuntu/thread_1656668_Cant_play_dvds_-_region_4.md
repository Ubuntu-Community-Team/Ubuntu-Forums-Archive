---
title: "Cant play dvds - region 4"
date: 2010-12-31
forum: New to Ubuntu
---

### Post by coward54 on 2010-12-31
Hello newbie here.  Running Ubuntu 10.10 in region 4 (australia)

I can't seem to play DVDs.  Movie player says it needs the right package or something, then I've been here, [https://help.ubuntu.com/community/Medibuntu#Adding%20the%20Repositories](https://help.ubuntu.com/community/Medibuntu#Adding%20the%20Repositories)

I added the Medibuntu repository at the above page, but it still says I dont have the right packages.  Is there something I'm doing wrong do I have to install something in the command line to get it working etc?

---

### Post by laithbsoul on 2010-12-31
well I'm not sure as i've never tried to play a region 4 dvd but have you tried vlc.

---

### Post by owiknowi on 2010-12-31
as far as i know the region code is a hardware thingy.

there must be a tool, believe for windos, to make your dvd player regio code free (use at own risk).
search on the web for remove regio code (brand pc or dvd player).

a workaround could be to copy the dvd to your hard disk and let the program remove the regio code as stored on your dvd.
search the web for rip dvd

hope this helps

---

### Post by cascade9 on 2010-12-31
You actually dont need to add the medibuntu repo- 

> **Installing libdvdcss**

 Legal Warning: Check with your local laws to make sure usage of libdvdcss2 would be legal in your area. 
 
**Ubuntu 9.04, 9.10, 10.04 (i386, amd64) and 10.10**

 
[LIST]
[*]Install the **libdvdread4** package (**no need to add third party repositories**) via Synaptic or command line: 
[/LIST]

 sudo apt-get install libdvdread4
[LIST]
[*]Then open a terminal window and execute: 
[/LIST]

 sudo /usr/share/doc/libdvdread4/install-css.shRebooting may be necessary. 

[https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs)

---

### Post by coward54 on 2010-12-31
Ok, but the dvd was a validly rented dvd, coded for region 4, so there's nothing underhanded I'm trying to do - not trying to bypass coding etc, just want to play the dvd I rented.  Find it surprising that ubuntu can't play these dvds.

---

### Post by coward54 on 2010-12-31
Actually I went to this link and typed the below code:

 sudo apt-get install libdvdread4

but then it said it couldn't find it.  
I found it strange that there was no actual source for the file

Is there a particular piece of software I need to play dvd's 
and is there a particular way of actually getting it to run on my computer
I get confuse with the command line, how do you actually install software?

---

### Post by owiknowi on 2010-12-31
did you try to add dvd software trough synaptic from ubuntu-restricted?

i use the default dvd player from ubuntu and it asks whether it can install missing codecs.

---

### Post by owiknowi on 2010-12-31
> **coward54 said:**
> Ok, but the dvd was a validly rented dvd, coded for region 4, so there's nothing underhanded I'm trying to do - not trying to bypass coding etc, just want to play the dvd I rented.  Find it surprising that ubuntu can't play these dvds.

that's because there is a region code in the firmware of your dvd player.

---

### Post by cascade9 on 2010-12-31
> **coward54 said:**
> Actually I went to this link and typed the below code:

 sudo apt-get install libdvdread4

but then it said it couldn't find it.  
I found it strange that there was no actual source for the file

Is there a particular piece of software I need to play dvd's 
and is there a particular way of actually getting it to run on my computer
I get confuse with the command line, how do you actually install software?

I have no idea why apt-get couldnt find the package. :( Are you sure you opened terminal? (I've seen people paste commands into gedit, etc in the past) 

To play  DVDs you'll need DVDCSS (DVD content scrambling system), which is what libdvdread4 is, and a video capable media player.  

You should be able to install software with ubuntu using software centre, synpatic, or command line. 

How does the commnad line confuse you? 

> **owiknowi said:**
> that's because there is a region code in the firmware of your dvd player.

Its nothing to do with the region code. If the OP is in region 4, and bought the computer/DVD drive in region 4, its going to be loaded with region 4 firmware....

---

### Post by coward54 on 2010-12-31
So to clarify, I went to this link:
[https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs)

I opened a terminal session, and typed in the following:
sudo apt-get install libdvdread4

But then it said it couldn't open the codec or something.....

What confuses me about the command line is that when I type the above 'apt-get' etc
where exactly is it going?  How can it go and just install software
like that - shouldn't it need to go to a particular place on the internet
etc to get it?

---

### Post by cascade9 on 2010-12-31
Try doing the 2nd command anyway (sudo /usr/share/doc/libdvdread4/install-css.sh)

> **coward54 said:**
> What confuses me about the command line is that when I type the above 'apt-get' etc
where exactly is it going?  How can it go and just install software
like that - shouldn't it need to go to a particular place on the internet
etc to get it?

No, thats one of the great things about a lot of linux distros, repositories (or 'repos'). Thats where they store software that you can install from a simple command (or from a GUI like software centre or synaptic). 

No need to go looking all over the net to find stuff, and possibly d/ling some dodgy software.

---

### Post by cascade9 on 2010-12-31
Annoying, things were dodgy. No idea if that was me or the forum...

Delete this post please.

---

### Post by cascade9 on 2010-12-31
Delete  Me!

---

### Post by cascade9 on 2010-12-31
Delete Me!

---

### Post by laithbsoul on 2011-01-01
> **cascade9 said:**
> Try doing the 2nd command anyway (sudo /usr/share/doc/libdvdread4/install-css.sh)



No, thats one of teh great thinsg about a lot of linux distros, repositories (or 'repos'). Thats where they store software that you can install from a simple command (or from a GUI like software centre or synaptic). 

No need to go looking all over the net to find stuff, and possibly d/ling some dodgy software.

indeed that is the true greatness of linux.

---

### Post by jmszr on 2011-01-01
coward54,

Just a thought. Click on System > Administration > Software Sources > Ubuntu Software and make sure that the first four (main, universe, restricted, and multiverse) boxes are checkmarked. If they weren't, after you checkmark them, run: sudo apt-get update  and: sudo apt-get upgrade  in the terminal. Then try running those commands again.

The only DVD player that I'm aware of that region locks up tight is the Matshita.

Again, just a thought.

---

### Post by Gone fishing on 2011-01-01
The region locking is also in the DVD hardware. This can usually removed by flashing the Drive with new firmware.

---

### Post by PatchesTheCaveman on 2011-01-01
Yes, you will need to follow jmszr's instructions.  Unfortunately, at least on Ubuntu 10.10 Maverick Meerkat, Software Sources is not on the Administration menu.  To get to it, run this command on the terminal:
```
gksudo software-properties-gtk
```
Make sure all the Ubuntu repositories are checked.

After that, you will need to run this command to update your computer with all the packages available from the new repositories:
```
sudo apt-get update
```

Then, run this command to get DVD playback functionality.
```
sudo apt-get install libdvdread4
```

I recommend using the VLC media player to play DVDs and other types of media.  I've never come across anything it wasn't capable of playing.  Install it by running:
```
sudo apt-get install vlc
```

The VLC developers have also [taken steps](http://www.videolan.org/developers/libdvdcss.html) to ensure that DVDs will play regardless of your drive's region settings.

---

### Post by jmszr on 2011-01-01
@PatchesTheCaveman,

I'd forgotten about reading this: [https://ubuntugenius.wordpress.com/2010/11/26/ubuntu-10-10-upgrade-how-to-re-enable-missing-software-sources-in-system-menu/](https://ubuntugenius.wordpress.com/2010/11/26/ubuntu-10-10-upgrade-how-to-re-enable-missing-software-sources-in-system-menu/) .

It seems that you have to enable the Software Sources listing in the Main Menu for it to show up under Administration.

---

### Post by Myglaren on 2011-01-01
I wish that I had seen this a year ago.
I bought [Home](http://www.youtube.com/watch?v=jqxENMKaeCU) and when it arrived it was region 1.
Nothing I had would play it.  Recently it came out in region 2 so I bought another copy and gave the original away.
Would have been nice to have known about the conversion capability. Presumably it also works for region 1 DVDs?  Haven't any to experiment with anymore :(

---

### Post by coward54 on 2011-01-06
Not having a lot of luck here:

david@david-K51AC:~$ sudo /usr/share/doc/libdvdread4/install-css.sh
sudo: /usr/share/doc/libdvdread4/install-css.sh: command not found
david@david-K51AC:~$ p-word
p-word: command not found
david@david-K51AC:~$ gksudo software-properties-gtk
WARNING: can not get name for '<gtk.TextBuffer object at 0xa618414 (GtkTextBuffer at 0xa2cb160)>'WARNING: can not get name for '<gtk.CellRendererText object at 0xa61843c (GtkCellRendererText at 0xa2cd898)>'
^C
david@david-K51AC:~$ 

SO I thinjk what i'm doing is getting access to a screen on Services panel, which will allow me to then see options regarding software,tick them all and then be able to run the package that installs css which allows movies to run.

am I on the right track?

---

### Post by jmszr on 2011-01-06
coward54,

Please go to System > Preferences > Main Menu > and checkmark Software Sources as described in this link: [https://ubuntugenius.wordpress.com/2010/11/26/ubuntu-10-10-upgrade-how-to-re-enable-missing-software-sources-in-system-menu/](https://ubuntugenius.wordpress.com/2010/11/26/ubuntu-10-10-upgrade-how-to-re-enable-missing-software-sources-in-system-menu/) .

Then go to System > Administration > Software Sources per post #13.

Hope that helps.

---

### Post by coward54 on 2011-01-10
Still no luck.
I did the necessary changes so I could see the software sources - all four were checked, multiverse etc etc.

I then ran 
david@david-K51AC:~$ sudo apt-get update

And that seemed to work, a huge amount of text spilled out on the terminal.

Then I typed 

 sudo apt-get install libdvdread4
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libdvdread4 is already the newest version.
libdvdread4 set to manually installed.
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.35-22 linux-headers-2.6.35-22-generic
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 31 not upgraded.

But now when I try to play a movie, it doesn't want to do anything, I can'tget movie player to do anything, when I click on the dvd, it just sits there, its like it doesn't recognize the file or anything?

Any ideas ? - might just have to go back to windows and try it there.

---

### Post by diablo75 on 2011-01-10
It doesn't look like anybody has suggested trying the Medibuntu repositories.

Just copy and paste this command into a terminal:

```
sudo wget --output-document=/etc/apt/sources.list.d/medibuntu.list http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list && sudo apt-get --quiet update && sudo apt-get --yes --quiet --allow-unauthenticated install medibuntu-keyring && sudo apt-get --quiet update && sudo apt-get install libdvdcss2
```

This will add the third party sources and then install the libdvdcss2 package.

Try playing a DVD after you install this.

---

### Post by cascade9 on 2011-01-10
Seems like you have DVDcss. Though you should try the other command as well (sudo /usr/share/doc/libdvdread4/install-css.sh)

If that doesnt work I'd try a different media player, just in case the one you are using is being silly.

---

### Post by coward54 on 2011-01-10
I tried that command, still doesn't play - what is dvdcss?  is that a type of player?

Is there another player I can download - the one I think I'm using is called 'Movie Player' ?



When I put the dvd in, it shows on the desktop, but then if I click autorun it wont do it. Then if I open up movie player, it shows the option 'play (name of DVD) in the 'Movie' menu, but then when you click on it, it just shows a menu with the movie listed on the left and you can't get it to do anything......

---

### Post by cascade9 on 2011-01-10
DVDcss (DVD content scrambling system), its what you need to decipher DVDs-

[http://en.wikipedia.org/wiki/Content_Scramble_System](http://en.wikipedia.org/wiki/Content_Scramble_System)

---

### Post by coward54 on 2011-01-10
I keep trying to open it with movie player, and it keeps saying it needs the 'dvd subpicture decoder'

is it really possible to play dvds on linux? maybe its just not possible with all the copyright stuff etc.....

---

### Post by coward54 on 2011-01-10
PS is there a way to see all threads on one page instead of multiple pages on this forum?

---

### Post by cascade9 on 2011-01-10
Its totally possible to play DVDs on linux, I do it fairly often....hmm, actually thats a lie, I normally rip them (no spinnign DVD drive noises). 

Seems that you might have hit a bug- 

[https://bugs.launchpad.net/ubuntu/+source/gstreamer0.10/+bug/545681](https://bugs.launchpad.net/ubuntu/+source/gstreamer0.10/+bug/545681)

From what is on that page, it seems like if you install gstreamer-plugins-bad the DVD should play. 

sudo apt-get install gstreamer-plugins-bad

---

### Post by coward54 on 2011-01-10
I tried that, I got this:
E: Unable to locate package gstreamer-plugins-bad

Do wonder whether linux can actually play dvd's - it might be new copy protection has ruled it out.

---

### Post by cascade9 on 2011-01-10
Doh, thats what I get for not checking the package name.... 

sudo apt-get install gstreamer0.10-plugins-bad

Linux can have problems with some new DVDs, but I'm pretty sure thats not the problem in this case.

---

