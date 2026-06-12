---
title: "Adobe Flash Player"
date: 2009-03-08
forum: New to Ubuntu
---

### Post by Weasel_Cottage on 2009-03-08
Hello

So I've got WUBI running at the moment, seeing if me bird and I like it before we install the proper thing. so far we like what we see.

Trying to get the BBC iPlayer (a streaming audio/video site) working and it says I need to download Adobe Flash Player.

1. If this website works in VISTA how come it doesn't work on UBUNTU? 

2. Can I access the softwhere that's in the VISTA side of my computer?

I've tried downloading it from the website following the instructions for Linux, to no avail. this is what hapens:

I go to [http://get.adobe.com/flashplayer/](http://get.adobe.com/flashplayer/) and select .deb for Ubuntu 8.04+ from the drop down. And click Install. A pop-up then appearers asking me if I want to Open or Save it. If I click Save, another pop-up titled Downloads appearers saying install_flash_player_10_linux.deb so I click on this. Another pop-up titled Package Installer tells me, error: wrong architecture 'i386'. this last message is in red, so it must mean something bad , right!?!? also an icon appearers on my desk top.

I'm new to this so if this sounds like it has a simple solution then I apolagise.

Thamks for your time

Ed

---

### Post by kansasnoob on 2009-03-08
I've only used Wubi briefly but you should still be able (while booted into your new Ubuntu installation) to go to Applications > Accessories > Terminal and and run the command:

```
sudo apt-get install ubuntu-restricted-extras
```

You will then have to restart Firefox or whichever browser you are using. Hopefully you'll then have a working Flash plug-in.

If not you may want to go to System > Administration > Synaptic Package Manager and in the "Search" box type flash.

Make sure that neither gnash or swfdec-mozilla (or swfdec-gnome) are installed. If they are mark them for removal and tick on apply.

I also find that adding the Flashblock plugin by going to the upper toolbar in Firefox and Tools > Add-ons > Get Add-ons and searching for and instaling Flashbloch 1.5.8 greatly improves flash performance in Firefox on Linux.

---

### Post by capnthommo on 2009-03-08
hi Weasel_cottage, this one can be a bit of a fiddle.  but it will work.  the wrong architecture i386 message is not a critical warning, its just that (i think) you have a 32 bit flash and a 64bit system (feel free to correct me if i am wrong) - i have had it too.  the ubun tu restricted extras will help.  there is also a pretty useful multimedia how to on the forums.  try a search (top right hand search box) on multimedia how to and it should show.  i will post the location for you if i can find it - i only used it a couple of days ago but wouldn't you just know it?
keep at it - you'll get it.
(EDIT) heres the link 
 [http://ubuntuforums.org/showthread.php?t=766683[/URL] 
that will take you to another thread which has a big how to on getting most multimedia things installed - i have found it pretty useful.

cheers
nigel

---

### Post by mc4man on 2009-03-08
Out of curiosity, are you running vista 64 bit? If so you probably have a 64 bit wubi install and I don't believe the adobe version of flash player is compatible with 64 bit browsers (yet)

If that's the case the above suggestion (ubuntu-resticted-extras) is your best bet

---

### Post by Kareeser on 2009-03-08
Sure it is :)

[http://labs.adobe.com/technologies/flashplayer10/](http://labs.adobe.com/technologies/flashplayer10/)

Installing it is a little more complicated, but still easy.

Download the file, extract it, and copy libflashplayer.so to /usr/lib/mozilla/plugins OR ~/.mozilla/plugins (preferred)

Done and done.

---

### Post by capnthommo on 2009-03-08
hi again.  one more thing.  - take a look towards the top of the beginners threads page - see the "sticky threads" section?  the last one of those entitled 'New to Ubuntu? Start Here...' click on that it will take you to a page which has a whole list of very useful how tos and help pages.  i have found them really good to learn my way round this o/s.  whether its learning the system or solving specific problems its worth a look there.
cheers again
nigel
ps oh, sorry if you've been using linux for years, but assumed from your post you were as new as i was a while ago - plenty of windows but no ubuntu. didn't mean to offend, if i did.):P

---

### Post by DucksAndDolphins on 2009-03-08
I had the same problem, but what I did was I went into the Add-Ons menu in Firefox and installed FlashBlock, and it worked for me!

---

### Post by nayab on 2009-03-08
> **Kareeser said:**
> Sure it is :)

[http://labs.adobe.com/technologies/flashplayer10/](http://labs.adobe.com/technologies/flashplayer10/)

Installing it is a little more complicated, but still easy.

Download the file, extract it, and copy libflashplayer.so to /usr/lib/mozilla/plugins OR ~/.mozilla/plugins (preferred)

Done and done.


I have only been on Ubuntu for 2 days (so greetings to all the helpful Ubuntu people out there). I got the 64 bit version of desktop ubuntu running on an AMD Athlon 64 so the symptoms described above tally with my own experiences this evening.

I found this link to the alpha release and there is a tar.gz archive and I can make it extract the shared library. However, I have 2 problems however.

1 I cannot copy it to /usr/lib/mozilla/plugins because of a permissions issue (so I will go away and work out how to log in as root)
2 I am not sure what -/.mozilla/plugins means as I have searched for that folder in "file system" and ".mozilla" doesn't exist. (Maybe it is time for me to go and read up on some of the conventions used when posting file paths).

Either way, I still have my "safety net" of XP installed on the same PC but I am looking forward to some 64 bit stability for the first time in over a quarter of a century. This is also my first post on the forum but I have found it invaluable so far for a beginner. Thank you everybody.

---

### Post by Kareeser on 2009-03-08
1. Yes, there is a permissions problem there, to protect the system from you :)

If you know what you're doing, or are guided by someone you trust (which, I suppose, in this case, would be me. Do you trust me? :)), then you can "tell" the computer so, by appending a command in front called "sudo". So, assuming libflashplayer.so is on your desktop:

```
sudo mv ~/Desktop/libflashplayer.so /usr/lib/mozilla/plugins/
```

2. Now, You'll notice that I again used the tilde "~" in the command. In Ubuntu, when used in the terminal/file paths, that character tells the system that you want to go to your home directory.

e.g.
```
cd ~/Desktop/
```

Tells the system that you want to go to the Desktop folder in your home directory.

HTH :)

---

### Post by nayab on 2009-03-08
> **Kareeser said:**
> 1. Yes, there is a permissions problem there, to protect the system from you :)

If you know what you're doing, or are guided by someone you trust (which, I suppose, in this case, would be me. Do you trust me? :)), then you can "tell" the computer so, by appending a command in front called "sudo". So, assuming libflashplayer.so is on your desktop:

```
sudo mv ~/Desktop/libflashplayer.so /usr/lib/mozilla/plugins/
```

2. Now, You'll notice that I again used the tilde "~" in the command. In Ubuntu, when used in the terminal/file paths, that character tells the system that you want to go to your home directory.

e.g.
```
cd ~/Desktop/
```

Tells the system that you want to go to the Desktop folder in your home directory.

HTH :)



Thank you. I trust you about as far as I can spit you out, but seeing as there is no valuable data on this particular PC, I am willing to give this a try and let you know.:D

---

### Post by nayab on 2009-03-08
Many thanks Kareeser. Worked like a charm.

I have just seen the link to the free Ubuntu Pocket guide. Some bedtime reading awaits me.

But also, going on the ~ symbol pointing to home, I do not have a folder called ~/.mozilla/plugins. You stated this was the preferred location of the shared library. Is there any reason why? Don't answer if the question is beneath you or you do not have the time/inclination. I will understand.:)

---

### Post by RomeReactor on 2009-03-08
Hi nayab. Just a comment on this: all files and folders whose names begin with a dot are hidden. To view them, press CTRL+H in Nautilus, and press that again to hide them. On a fresh Ubuntu install, the folder is not there until you run Firefox at least once.

Regarding the location of the plugin, if you put it in /usr/lib/mozilla/plugins it will be available to any user on that computer; if you put it in ~/.mozilla/plugins it will only be available for your account.

---

### Post by Kareeser on 2009-03-08
It's up to personal choice, as Firefox checks both directories for plugins.

I chose ~/.mozilla/plugins/ (or in its full incarnation on my machine: /home/julian/.mozilla/plugins/) because I can better keep a track of changes, since it is _my_ home folder.

Come to think of it, because I keep it in my home folder, the plugin MIGHT not be available to other users of the computer... but because I am the only user, it is a moot point.

If you want to get into the nitty gritty details... there exists an informal heirarchy as to where files go. If they don't go in the right place, nothing bad happens, but it just makes things harder to find in the long run. Where you choose to place these files is ultimately up to you, and what you want to achieve :)

Best of luck!

Edit: RomeReactor answered my query. Thanks!

---

### Post by nayab on 2009-03-08
Many thanks to both of you guys. I feel more educated already. It is just me. The more I have things explained to me like I am an idiot, eventually, the last piece of the puzzle goes into place and then I can take off on my own. You have been very patient. Thank you again.

---

### Post by gandaran on 2009-03-09
> **DucksAndDolphins said:**
> I had the same problem, but what I did was I went into the Add-Ons menu in Firefox and installed FlashBlock, and it worked for me!
do you know what flashblock add-on is for? I don't think you do!

---

