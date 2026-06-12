---
title: "Accessing/watching dvd movie"
date: 2009-09-20
forum: New to Ubuntu
---

### Post by mjp29 on 2009-09-20
I think the computer I'm using (was given) has a dvd player/burner built in.

here is what I have [http://h18000.www1.hp.com/products/quickspecs/11876_div/11876_div.HTML#Storage](http://h18000.www1.hp.com/products/quickspecs/11876_div/11876_div.HTML#Storage)

When I put a dvd movie in, how do I view it

(perhaps i don't have a dvd player/burner - any command line i can type into terminal to check this)

---

### Post by scrooge_74 on 2009-09-20
Hi,

first start [here]("http://ubuntuforums.org/showthread.php?t=766683"), questions, ask away

---

### Post by muddles on 2009-09-20
you need to install the Ubuntu-Restricted-Extras  and  libdvdcss2...from the Synaptic package manager

-it contains the information neccessary to decode encrypted DVDs (CopyRight Protection)
and other Copy Protected formats

Below might help too
[https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs).


This is the Note for the Restricted Extras 
Please also note that packages from multiverse are restricted by copyright
or legal issues in some countries. 

you also would want to install VLC Player , it has better functionality than Totem and other media Players.

---

### Post by mjp29 on 2009-09-20
Where is the Synaptic package manager

I copy and pasted all the code lines into terminal from the help links in above threads and no luck

Perhaps my player is only CD

any command line to check if I actually have a dvd player/recorder

---

### Post by qjqqyy on 2009-09-20
> **mjp29 said:**
> Where is the Synaptic package manager

I copy and pasted all the code lines into terminal from the help links in above threads and no luck

Perhaps my player is only CD

any command line to check if I actually have a dvd player/recorder?

synaptic is at System>Administration>Synaptic Package Manager
just check your hardware
that's simple enough

---

### Post by mjp29 on 2009-09-20
I installed everything and I believe my built in drive is CD 

So I plugged up my external DVD drive and Ubuntu recognized it and asked if I wanted to use movieplayer (or other program) to open in by default

My problem now is that when I try to get movie player or other players to play the dvd movie, the movie doesn't play.

Perhaps the cord that I'm connecting the dvd drive to the PC is a usb 1 cord (is that possible) and I need to buy a usb 2 cord to hook it up?

hmmmm

---

### Post by sandyd on 2009-09-20
> **mjp29 said:**
> I installed everything and I believe my built in drive is CD 

So I plugged up my external DVD drive and Ubuntu recognized it and asked if I wanted to use movieplayer (or other program) to open in by default

My problem now is that when I try to get movie player or other players to play the dvd movie, the movie doesn't play.

Perhaps the cord that I'm connecting the dvd drive to the PC is a usb 1 cord (is that possible) and I need to buy a usb 2 cord to hook it up?

hmmmm
usb 2 is backwards compatible with usb1
you can plug a usb 2 cable into a usb 1 device and a usb 1 cable into a usb2 port
doesn't make a difference except for the speed.

---

### Post by mjp29 on 2009-09-20
I suppose my problem may be that I have an older usb 1 cord (for a printer) that I'm using to hook up this external dvd drive.

I can access the files on a dvd movie disk; however, when I tell moveiplayer to play the movie, movieplayer ubruptly quits.

Perhaps the cord needs to be usb compliant to play dvd movies - ?


I just tried a different dvd movie and now get message Totem is unable to open and "DBus error org.gtk.Private.RemoteVolumeMonitor.Failed: An operation is already pending"

also, within movie player I get the error "Could not open location; you might not have permission to open the file."

Update:  on the side of both usb cords i've tried say they are both usb 2.  have tried playing 3 movies and none will play

---

### Post by jmszr on 2009-09-20
mjp29,

You should install Medibuntu: [https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu).

Then,you should install:```
sudo apt-get install libdvdcss2
```

And, if you haven't already:```
sudo apt-get install ubuntu-restricted-extras
```

And, if you haven't already:```
sudo apt-get install vlc
```

VLC will play almost anything.

---

### Post by scrooge_74 on 2009-09-20
> **mjp29 said:**
> I suppose my problem may be that I have an older usb 1 cord (for a printer) that I'm using to hook up this external dvd drive.

I can access the files on a dvd movie disk; however, when I tell moveiplayer to play the movie, movieplayer ubruptly quits.

Perhaps the cord needs to be usb compliant to play dvd movies - ?


I just tried a different dvd movie and now get message Totem is unable to open and "DBus error org.gtk.Private.RemoteVolumeMonitor.Failed: An operation is already pending"

also, within movie player I get the error "Could not open location; you might not have permission to open the file."

Update:  on the side of both usb cords i've tried say they are both usb 2.  have tried playing 3 movies and none will play

Did  you went through the multimedia instructions ?  Try copying the movie into your hard drive you can test it without having to deal with usb problems

---

