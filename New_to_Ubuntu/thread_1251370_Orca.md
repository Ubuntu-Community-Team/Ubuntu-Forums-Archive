---
title: "Orca"
date: 2009-08-27
forum: New to Ubuntu
---

### Post by fleamour on 2009-08-27
I've installed Orca within Xubuntu Jaunty for a dyslexic friend, but cannot see any entry within applications?  Alt F2> "orca" also draws a blank.  

Where am I going wrong?  Is Orca only for the Gnome desktop & will not work with Xfce?

---

### Post by QIII on 2009-08-27
Bad news...

[https://bugs.launchpad.net/ubuntu/+source/gnome-orca/+bug/347113](https://bugs.launchpad.net/ubuntu/+source/gnome-orca/+bug/347113)

Not sure when this will be resolved, or if it has been and I am just not finding it.

---

### Post by fleamour on 2009-08-27
Ah OK thanks.  He uses Thunder under Win2k at the moment, come July 2010 2k will be an unpatched OS.  Buuut, looking at the minimum requirements for plain old Ubuntu as opposed to Xubuntu I might as well install that.

---

### Post by QIII on 2009-08-27
The Ubuntu/Xubuntu choice is really one of preferences if you are not concerned about specs.  Gnome or XFCE interface.

Everyone has their preference...

---

### Post by Hospadar on 2009-08-27
There are other TTS alternatives, perhaps not as well integrated as orca, but enough where you can copy paste text and have a cool robot voice say it back to you.

You can use the kde (ktts?) tts program or others.  Google around/search in synaptic.

That said, I just installed and ran orca alright in 64 bit KDE, so maybe a fresh install (if possible) of a different flavor would help, or perhaps try hunting down missing dependencies.  Sometimes package maintainers make assumptions about what packages will be installed and something gets missed on the dependancy list.

I would give regular ubuntu a go and see how well it runs, I've had good luck with it even on pretty low-powered systems.

---

### Post by fleamour on 2009-08-27
Well it's a PIII 800MHz laptop with 512MB of RAM so hopefully adequate.

---

### Post by djringjr on 2009-08-29
If using Alt Ctrl F1 brings open the virtual console and typing 

orca

does not start Orca, then simply orca is NOT installed.  I'm using Orca right now with Ubuntu Kosmic Koala (fully updated) in the 64bit version.

Here is the fix.

Bring down the console.

Log in with the user name press ENTER then type in the pass word and press ENTER.

Then type

```
sudo su
```

You will be asked for the user's password - please type it in and press ENTER.

If successful (you entered the correct information) you will see the new prompt starting with # instead of the user prompt with starts with $.

Then type

```
aptitude update
```

HINT:  In the console mode, you can type the first few letters of the command - say you misspell aptitude sometimes :-) and apttitudde just doesn't load anything, you can type apt and then press TAB you will hear an error beep.  This means there is more than one command starting with apt.  Press the TAB key again and you will see the rest of the posibilities in the console.   You will also see the command line still with what you typed in at the bottom.  Looking at the list you see all the commands starting with apt - and you see that if you type in the letter i you will then be able to press the TAB key and the console will self complete the command!!!

After typing in aptitude update type this:

```
aptitude install orca
```

You need to refresh aptitude before installing any program to be sure you have the new programs and updates.

You should see the screen "flash" with lots of writing - if you don't see the magic word "Error" don't worry - everything is going as planned.

Now type this to go back to the user mode:

```
exit
```

It is important to do most everything you can in the user mode with the $ prompt because doing so does NOT allow you to change the system files - user mode protects you from making changes that could stop your operating system from working correctly.

But there are times that you NEED to go to the administration prompt which is # - it is called the "root" prompt and it can change settings which are above the user's "home" file system.

This should get your Orca working.

If you have any problems - post them here!

You might also like to download a iso file of Vinux 1.3 which is based on Ubuntu - it was developed for the blind users of Ubuntu.

I used to use Vinux 1.3 because it had suport for the Broadcom wireless network card in my notebook.  I think I had problems with later versions of Vinux.

Here is the link for Vinux 1.52
[http://linux.softpedia.com/get/Adaptive-Technologies/Vinux-43337.shtml](http://linux.softpedia.com/get/Adaptive-Technologies/Vinux-43337.shtml)

You will see a button for download, but just in case you don't see it here it is:

[http://vinux.org.uk/downloads/old/1.52/Vinux-1.52.iso](http://vinux.org.uk/downloads/old/1.52/Vinux-1.52.iso)

Tony Sales and the Vinux Development Team have decided to base further development on Debian because of a problem with Ubuntu's default audio server "pulseaudio". 

There is a simple work around for doing this though.

When installing Ubuntu, at the start up screen, select Accessibility and then select "screen reader" this will NOT install pulseaudio and will change the sound settings so that Orca will run without the problems of using pulseaudio.  Orca will use ALSA sound instead.

But first follow this message - I will direct you to any pages that you might need or you might search google for ```
"remove pulseaudio" ALSA orca
```

But that's in the future!  First get orca installed for your friend!

Best wishes,

David Ring
Green Harbor, MA
[www.qsl.net/n1ea](www.qsl.net/n1ea)
-30-


Best wishes from a happy user of Orca.

---

### Post by fleamour on 2009-08-29
Hi

Orca will run with setup options within virtual console (Alt + Ctrl + F1).  But it does not appear to be available from the desktop?  I ran your fix in the terminal whereupon it uninstalled some stuff.  Did you mean to run fix from within the virtual console?  Please clarify, never heard of virtual console 'till today!

:D

---

### Post by fleamour on 2009-08-29
Also, I was hoping to get Orca to read highlighted text when pressing a certain key combo, as opposed to running all the time.  Not sure if it works like this?

---

### Post by fleamour on 2010-08-04
Still does not work with Xubuntu, am gonna try a test installation of Ubuntu.

---

### Post by djringjr on 2010-08-04
> **fleamour said:**
> Still does not work with Xubuntu, am gonna try a test installation of Ubuntu.

Vinux - a derivative of Ubuntu - has hand picked programs that are accessible.  Vinux is for the visually impaired / blind user as well as the general user.  It has two magnifiers, and three screen readers.  ORCA, SpeakUp and YASR.

[http://distrowatch.com/table.php?distribution=vinux](http://distrowatch.com/table.php?distribution=vinux)

The only accessible Desktop is GNOME which Vinux uses.

It will run on 512 MB or RAM, but 1 GB is better.

Be well,

David

---

