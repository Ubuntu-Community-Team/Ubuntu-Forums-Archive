---
title: "&quot;Huston, we have a problem&quot;  sd card, download"
date: 2009-04-26
forum: New to Ubuntu
---

### Post by konza on 2009-04-26
First allow me to say i am a copy/paste terminal user(KISS, Keep It Simple Stupid).  This suits me fine as i do nothing exotic on the computer.  A little music with gnutella, access to my company's website, and web surf for instructionals or things of interest.  I like Ubuntu as it asks me to learn a little bit about the machine i use.  Anyway I wanted to try Debian on a sd card just to see what Ubuntu is based on.  So off to UNetbootin i went.  I installed 8.10 long ago this way and kept it's sd card.  Used the same procedure with Debian, clicked the distro button on unetbootin and seen that the file was directed to the sd card.  It downloaded and went through the auto-install.  
   After the start sequence(verbose)it asked for -Debian login & password- Umm, I entered no name or password when it installed.  Save for giving the package manager permission at the very beginning.  I can select either Debian or Unbutu at start up...as amatter of fact i have to.  If i let it go default it boots Debin then hangs on the password thing. I've tried my sudo login and password and in every combination and case (just incase i hit caps lock accidentally.  No luck. 
   So i pulled the sd card thinking i would go back to 8.10 and try something else...but now the computer(hp mini 1030nr) will only boot with the sd card w/Debian in it.  Without the card I get the message  ERROR 17  Odd thing is the computer runs fine without the sd card w/debin if i remove it AFTER boot up.  
   I tried something but to no avail.  Since 9.4 is out i upgraded to it(via update manager) after booting and removing the debian sd card.  Computer still needs the sd card to boot.  Grrrrr.
   How can i undo this snafu with the sd card?  Please remember i am a cut and paste kid.  Not afraid to reformat the whole works, but would like to unsnarle it if a can.  Help !

---

### Post by Didius Falco on 2009-04-26
So you can get into Ubuntu by using the Debian sd card until after it boots?

If so, what's happened is that Grub has been written to the Debian sd card. Boot into Ubuntu, open a terminal and paste ```
sudo grub
```This will load the grub program. Then paste ```
find /boot/grub/stage1
```without the Debian card in, it should just have the location of your Ubuntu grub install. It'll return a value like "hd0,2" - note that this will differ depending on your pc.

You'll use this value in the next command:

```
root (hd0,1)
```Again, it may be different than the example above. Use the value returned from the Find command.

Then paste in ```
setup (hd0)
```You should get some output telling you that it found the grub boot info. Type ```
quit
``` and then reboot.

Try it without the sd card in, and it should boot into Ubuntu. You can then proceed to the Debian forums and find out how to reset the username and password, and get the info to add the Debian boot-up info needed to add to the Ubuntu "menu.lst" file.

I hope this helps...

---

### Post by konza on 2009-04-26
Thank you for helping Falco,  Following your instructions gave me hd0,0 , followed cut and paste.  Now it gives me a ERROR 21. Just for giggles i ran the commands with the debian card in as well as out.  No luck but we are on the right track.  Have to go to work this evening but will keep at until it is right.  THank you again !!!!

---

### Post by Didius Falco on 2009-04-26
Is the pc booting into anything at all now?

On Edit: The simplest way to fix this may be to download the Super Grub Disk and use that. Here is the website, which has links to the downloads, documentation, etc.

[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/) 

It's not that I mind helping you, it's just that it can be hit or miss as to when I'm here, and I don't want to leave you hanging.

Try out the Super Grub Disk and post back how it's going. I'm invested in this one, now. <G>

---

### Post by Didius Falco on 2009-04-27
Hi Konza,

I still, after some sleep, think it'd be a good idea to have a copy of the Super Grub Disc handy, but I'd also like to see some info from your pc.

Let me know what, if anything, loads up, and we'll go from there. Maybe someone that knows more than me will jump in as well...

---

### Post by konza on 2009-04-28
Hi Falco
     Thanks for again for trying to help me figure this thing out.  To answer one question,  yes the machine boots up fine.  But it still defaults to Debian which is password protected from ME for the time being.  I can f9 it and choose whether debian or ubuntu if i catch it before it does the default thing.  Ubuntu, when chosen, does fine.  I can even unmount the debian sd and it keeps on working great.  It just has to have the deb sd card to boot.  
   I am wondering if somehow the debian install "stole" my ubuntu boot/grub.  To refresh, i got the Error 17 befor i used your suggestion when i tried to boot to ubuntu,  got Error 21 after trying to setup hd0,0(which the find command showed).   I guess it's sort of "same thing, different day"  Thinking back the only thing i entered during the deb install was YES to the option if i wanted the choice of system to boot to. 

    We will definitely give Super Grub Disc a try.  I may be slow getting back tho,  I'm in a two day operating rules re-exam class at my job (yuck).  Will talk to you later and let you know what Super Grub did for me.  
many thanks
mick

---

### Post by Didius Falco on 2009-04-28
You have the right idea - it's not a dire emergency, since you can get into both, so concentrate on your re-exam.

---

### Post by konza on 2009-04-29
Hi Falco,  Rules are over for another 2 years, back to my problem.  I did get Super Grub Disc and ran it. I did get error 17 back(remember when i tried to reset the grub it went to 21?)  anyway, when running the SGD i got the an Error 6.  Argh, that amounts to missing or corrupt stage1/ or 2/.  Beginning to wonder if it is in my abilities.  Going to Debian forums and see if there is a password recovery or something. Maybe i can work backwards.

---

### Post by konza on 2009-05-06
Ok, tried everything SGD instructions suggested.  No luck, but it may have been my nievity using commands.  I was getting in over my head, gave up and took the easy way out... reformat with Jaunty :(  I know it wasn't the best way but now i can start over from scratch and see if anything was omitted.  I won't leave well enough alone but try again until i get both systems working proper.  Thanks again Falco !!!

---

### Post by Didius Falco on 2009-05-06
> **konza said:**
> Ok, tried everything SGD instructions suggested.  No luck, but it may have been my nievity using commands.  I was getting in over my head, gave up and took the easy way out... reformat with Jaunty :(  I know it wasn't the best way but now i can start over from scratch and see if anything was omitted.  I won't leave well enough alone but try again until i get both systems working proper.  Thanks again Falco !!!

No problem. I'm still curious - there has to be a way to gest past that Debian no account problem. Maybe if you'd booted into whatever their version of Recovery Mode is, you could have used root to either look up the existing accounts or simply add a new one. Then you could have used that account to fix the other one, or just deleted it.  I can't let it go - this kind of thing makes me want to KNOW!!<G>

Anyway, glad your Ubuntu install is working well. As far as breaking stuff, that's how I learn the most.

Regards,

Didius

---

