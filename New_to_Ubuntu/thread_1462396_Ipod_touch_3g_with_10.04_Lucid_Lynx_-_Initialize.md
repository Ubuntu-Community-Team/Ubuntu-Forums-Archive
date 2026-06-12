---
title: "Ipod touch 3g with 10.04 Lucid Lynx - Initialize ???"
date: 2010-04-25
forum: New to Ubuntu
---

### Post by Petter72 on 2010-04-25
Hello,

I have a brand new iPod that I want to use with Lucid Lynx, i.e transfer music from my laptop to the ipod.
I keep reading that there is out-of-the-box support for ipod with Lucid Lynx and Rhythmbox.
Before I go on, I have to mention that I have never done anything with the ipod and I am not able to turn it on, I just get the same logo of a cable pointing to a CD with 'itunes' written underneath whenever I try to turn it on.
In Rhytmbox, I press Music->Scan Removable Media, then I get a dialogue box asking if I want to initialize the ipod. I cannot select the model, but I can type a name, which I do. I then press intialize, but nothing happens. I dont see the ipod in Rhythmbox, there is no icon, nothing.

Can anyone help me with this ? Do I have to initialize the ipod before I can access it ? How do I do that ?

---

### Post by Petter72 on 2010-04-25
One thing I forgot to mention was that I can see the ipod filesystem with the filemanager, I was even able to copy a music file onto it, which I can play back from the ipod using the totem movie player (0.2).
When I try to open the song with Rhythmbox I get the same message box asking me if I want to initialize the ipod

---

### Post by Temposs on 2010-04-25
The best way to get an ipod that doesn't work on Ubuntu/Linux is to get a "brand new ipod". If you want to use one with Linux, the older the better.

According to the primary ipod compatibility developer for linux, you currently must jailbreak your ipod touch if you want it to work with the Ubuntu software like rhythmbox. My source is here: [http://www.gtkpod.org/libgpod/](http://www.gtkpod.org/libgpod/)

> There's also preliminary support for the iPhone and the iPod Touch but they must be jailbroken to work. You'll find more details in the NEWS file.

Basically everyone uses that same ipod compatibility software, so it won't really help you much to try different players.

---

### Post by tom.swartz07 on 2010-04-25
NOPE NO NYET NAY NEIN!

You dont have to jailbreak your ipod. There are a few good guides there that are really up to date and allow you to sync your iPod with versions of Ubuntu before 10.04. [http://www.webupd8.org/2010/01/easy-way-to-sync-your-iphone-with.html](http://www.webupd8.org/2010/01/easy-way-to-sync-your-iphone-with.html) is a good one.


**EDIT: Schnikes. I didnt realize that you had 10.04 already. Are you sure your computer is up to date?**

If what information does it show when you first plug in your ipod? Was it formatted on a Mac or a PC?

---

### Post by Temposs on 2010-04-25
Seems like some ipod 5g support has been added recently, so ipod touch may work now:

[http://gtkpod.git.sourceforge.net/git/gitweb.cgi?p=gtkpod/libgpod;a=blob_plain;f=NEWS;hb=HEAD](http://gtkpod.git.sourceforge.net/git/gitweb.cgi?p=gtkpod/libgpod;a=blob_plain;f=NEWS;hb=HEAD)

And Ubuntu Lucid does indeed have the most recent version of libgpod. My wife has an ipod shuffle 5g, and I don't see any fixes related to that in the changelog. I think it's a bit of a strong statement to say there is full ipod support in Lucid Lynx. libgpod still has a lot of work to do, methinks.

---

### Post by orphanlast on 2010-04-25
Download virtualbox from virtualbox.com. Then download windows on it. Then download itunes. Work with that for now, to get your phone up and running.

From what I heard, a program called songbird is compatible with the ipod too.

---

### Post by Temposs on 2010-04-25
> **orphanlast said:**
> Download virtualbox from virtualbox.com. Then download windows on it. Then download itunes. Work with that for now, to get your phone up and running.

From what I heard, a program called songbird is compatible with the ipod too.

Songbird uses the same libgpod for ipod compatibility. As I said previously, it doesn't help much to try different players for ipod support, because they pretty much all use the same thing.

Besides, Songbird has ended its Linux support, so I wouldn't recommend using that.

EDIT: Regarding Virtualbox, that's what we do now. Works alright, but it's a pain to start up all that infrastructure just to put some songs on an mp3 player.

---

### Post by Petter72 on 2010-04-25
I initialized my brand new ipod 3G using windows and itunes and copied a few songs over to it. I then booted up Ubuntu and voila !!! The ipod is automatically recognized when I plug it in.
The point which confused me was the "out-of-the-box" support of 10.04.
The part which seems to be missing from this is the initialization. Other than that it works perfectly.

---

### Post by Temposs on 2010-04-25
Very cool. Glad you got it working :-) Please mark the thread as SOLVED.

---

### Post by gobble on 2010-06-19
Sorry, but I have an iPod touch 3g 32GB. Amarok 2.3 sees nothing. Rhythmbox sees nothing. It is mounted using ifuse and I can copy files from the file manager. 

Scan > removable devices does absolutely nothing. 

I'm on Kubuntu 10.0.4.

iPod 3.1.3 jailbrroken with Spirit.

Edit: And gtkpod sees nothing as well! 

Any ideas?

Regards

---

### Post by Temposs on 2010-06-19
The jailbroken ipod touch may not work with the media players like rhythmbox or amarok, maybe only non-jailbroken ones, because it's expecting to see a standard ipod touch signal, and it's not now that it's jailbroken. The 'broken' part of that word should be taken seriously, before doing it.

So, unless you can restore the original firmware & software on the ipod touch, you may only be able to use the file manager to deal with your ipod now.

---

### Post by gobble on 2010-06-19
OK, my /media/ipod folder was not mounting for some reason, hence the problem.

Now it works. Only photos cannot be copied. Music is ok :D

Cheers

---

### Post by gobble on 2010-06-19
Found Gwenview does  the job of managing photos from ipod. 

Now finally I have 3 major things working - videos copied and download, music and photos. Installed a lot of bloatware on my lucid before I discovered what works. Now I dont know what to uninstall safely to reduce the trash lying around my disk, but thats another challenge. 

Funnily no google search threw a page that said Gwenview does it!! I spend 30 mins before hitting it by fluke!!

Thanks for responding !!

Regards

---

### Post by gobble on 2010-06-19
> **Temposs said:**
> The jailbroken ipod touch may not work with the media players like rhythmbox or amarok, maybe only non-jailbroken ones, because it's expecting to see a standard ipod touch signal, and it's not now that it's jailbroken. The 'broken' part of that word should be taken seriously, before doing it.

So, unless you can restore the original firmware & software on the ipod touch, you may only be able to use the file manager to deal with your ipod now.

It works just fine jailbroken . No problems here. Thanks for responding :)

Cheers

---

### Post by HeWhoE on 2010-08-15
> **Temposs said:**
> The jailbroken ipod touch may not work... The 'broken' part of that word should be taken seriously, before doing it.

The *broken* part of the word *jailbroken* does not mean *inoperative because of damage, wear, or strain*. The *broken* here means *freed by overcoming restraints or constraints*.

When you *break* out of jail, you're *free*ing yourself from the restraints of the jail cell.

---

### Post by Veloteuton63 on 2010-08-29
> **Temposs said:**
> Seems like some ipod 5g support has been added recently, so ipod touch may work now:

[http://gtkpod.git.sourceforge.net/git/gitweb.cgi?p=gtkpod/libgpod;a=blob_plain;f=NEWS;hb=HEAD](http://gtkpod.git.sourceforge.net/git/gitweb.cgi?p=gtkpod/libgpod;a=blob_plain;f=NEWS;hb=HEAD)

And Ubuntu Lucid does indeed have the most recent version of libgpod. My wife has an ipod shuffle 5g, and I don't see any fixes related to that in the changelog. I think it's a bit of a strong statement to say there is full ipod support in Lucid Lynx. libgpod still has a lot of work to do, methinks.


gtkpod works fine with ipod 5G - for pictures and music.
I also used an ipod 3g with gtkpod - works good for the music.

But: as far as I know, your Ipod needs to be initialized on a windows machine -  Initialized on a MAC it sure does not work.

Does anyone out there as a solution ready at hand to manage videos on an ipod touch?

---

