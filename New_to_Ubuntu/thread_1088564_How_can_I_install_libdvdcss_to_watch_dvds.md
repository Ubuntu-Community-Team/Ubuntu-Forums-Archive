---
title: "How can I install libdvdcss to watch dvds?"
date: 2009-03-06
forum: New to Ubuntu
---

### Post by Ricardoubu on 2009-03-06
Just installed Ubuntu 8.04 in AMD2 computer with an integrated ASUS graphic card. 

Everything seems quite nice but cannot play dvds
I tried the advises I could but no way. Apparently, **libdvdcss** is essential. I downloaded it from here 

[http://videolan.org](http://videolan.org)

but **do not know how to install it or make it work**
I also installed vlc media player and does not work either.
And tried to find in synaptic libdvdcss2 but could not find it.

Any suggestion? Please explain it as you would for a [COLOR="Red"]**recent landed alien**[/COLOR], as I am a Windows user with quite limited computer knowledge (not programming and, as I said, new to Linux)



Many thanks!

---

### Post by arochester on 2009-03-06
Install the Medibuntu Repository. Instructions here: [https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

Note that it is a 2 part installation - 1) Install repository 2) Get GPG key

The package, properly called libdvdcss2, will appear in your available packages, to be installed from there.

---

### Post by orethrius on 2009-03-06
If you can state which file you downloaded (and to where), I can craft a line for the Run prompt that should handle the situation. ;)

[quote=arochester]The package, properly called libdvdcss2, will appear in your available packages, to be installed from there.[/quote]

Assuming he has no knowledge of Synaptic, it's under System > Administration > Synaptic Package Manager.  After Medibuntu repositories are activated per arochester's link, you can just start typing **libdvdcss2** in that program (Synaptic) and the package will be found for you.  Simply click the checkbox left of its name, click "Mark for Installation", and click Apply.  If you're asked to install other supporting packages, click Accept or Enable as appropriate.

---

### Post by chamber on 2009-03-06
This worked for me.

In the terminal type,

```
sudo apt-get install vlc libdvdcss2 ubuntu-restricted-extras w64codecs
```

this will download the codecs, if you have the restricted extras then you may already have them.

Then,

```
cd /usr/share/doc/libdvdread3/
sudo ./install-css.sh
```

The dvds should now be able to be played.

---

### Post by Ricardoubu on 2009-03-06
Next problem related to the first:

When I tried to insert sudo commands at Terminal, I was asked for my password. I tried to type it but could not type anything. Tried three times and got a warning. Will not try again without advise!

---

### Post by linuxisevolution on 2009-03-06
> **Ricardoubu said:**
> Next problem related to the first:

When I tried to insert sudo commands at Terminal, I was asked for my password. I tried to type it but could not type anything. Tried three times and got a warning. Will not try again without advise!

You will not be able to see the password as you type. Imaging that it is invisible. Simply type the password and hit enter. This is a security feature so people can't spy on you over your shoulder.:)

---

### Post by Ricardoubu on 2009-03-06
Guys, you are absolutely amazing! With a bit of every of the advises I could manage to make it run, and best of it, I have learnt a bit of this stuff.

Many thanks to all of you!

PD how can I indicate that the problem is solved? Or is it the administration who does this?

---

### Post by carml on 2009-03-06
You can, at the moment, change the title of your post to let people know that you solved your problem.
P.S. To view DVD you have also take a look in System->Hep & Support -> Music,Video and Photographs, to ensure yourself you have got all the necessary to play DVDs.:)

---

### Post by swoody on 2009-03-06
Ricardoubu, Welcome te Ubuntu, and to the Forums!! ):P

For a little more how-tos about installing any mutimedia stuff, you can check out this link:
[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)
There is a section under there for how to play DVD's and how to set your default DVD player that will auto-load when you insert a DVD.

As far as being able to mark a thread as [SOLVED] it's temporarily disabled:
[http://ubuntuforums.org/showthread.php?t=1044714](http://ubuntuforums.org/showthread.php?t=1044714)

Again, welcome to the Forums!:)

---

### Post by Ricardoubu on 2009-03-06
> **carml said:**
> To view DVD you have also take a look in System->Hep & Support -> Music,Video and Photographs, to ensure yourself you have got all the necessary to play DVDs.:)

Thanks. It seems I can play DVDs, yes. Though, I will check what you suggest.

Many thanks again to all of you.

Best

Ricardo

---

### Post by chamber on 2009-03-06
Your welcome.

Have fun with Linux!!

---

