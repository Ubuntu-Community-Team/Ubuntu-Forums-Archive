---
title: "Keyboard layout reverting to US on (every) reboot"
date: 2010-02-24
forum: New to Ubuntu
---

### Post by JamesParnell on 2010-02-24
I live in the UK, and have the default UK keyboard, with the layout as US on ubuntu, so I changed it to UK, deleted the US one, applied System-wide. which was fine until it rebooted, then it went right back to US...why is that?...and how can i fix it?

---

### Post by boxcorner on 2010-02-24
What I did is: 
System > Preferences > Keyboard preference > Layouts tab
Select keyboard model
Select layout United Kingdom
Apply system-wide
£ above 3 works for me
If that's what you're trying to achieve
Hope that helps

Addendum [Friday, 26 February 2010 10:29 AM]
There's an option for selecting the keyboard at the bottom of the login screen.

---

### Post by s1wood on 2010-03-22
I have exactly the same problem with my new install. I've done the 'preferences' bit and removed the USA option but  it reverts at every boot.
I have automatic log-in so I don't see the log-in screen.

Any known way of removing the USA keyboard permanently?

Susan

---

### Post by MrNatewood on 2010-03-23
Similar problem.
Set layouts to
-USA Internations(AltGr dead keys)
-Israel

And it resets every boot to USA.

I should add that clicking on "Reset to Defaults" applies my chosen layouts. but again reverts to USA after reboot.

What configuration file does ubuntu "ask" to find out which layouts to set at boot?

I am using Karmic 64.

---

### Post by s1wood on 2010-03-23
Strangely, mine has worked OK since I complained about it!

Susan

---

### Post by vratnica on 2010-03-24
similar problem

my default is bosnian layout, with german as additional one

every time I reboot, it switches to some strange layout which doesn't give me letters but some strange symbols. So I always have to remove that stupid layout called ba, de

Any solution?

---

### Post by ianmackinnon on 2010-03-24
I have similar problems on two computers running 9.10.

I would like to have just UK and Latin American layouts installed but I keep being attacked by zombie keyboard layouts.

On my desktop (shere the system language is Spanish) every time I login the Spanish (ES) layout has been added and is selected even though I remove it every time.

On my netbook (system language English) every week or so a ghost layout appears as '??' in the system tray icon and produces a seemingly arbitrary group of symbols.

Does anyone know what parts of the OS have the capacity to install new layouts and how to determine which one is responsible?

Any help appreciated!

---

### Post by c.j.stephen on 2010-03-25
I found the same problem, but only on my wife's account. I'd set her keyboard layout to UK through Gnome preferences and every time the US layout would reappear and be selected frustratingly.

It turned out that on the gdm login screen her choice of keyboard layout in the discreet option bar at the bottom of the screen was set to US. That was then overriding the Gnome layout preference.

Solution: Selecting the appropriate keyboard layout on the next login solved the problem and GDM remembered the preference for next time.

This isn't what the user would expect to happen. Is there a way to unify / synchronise the GDM and Gnome keyboard layout preferences ?

---

### Post by vratnica on 2010-03-25
well, I don't have any login screen :confused:

---

### Post by littlesatan on 2010-03-25
> **vratnica said:**
> well, I don't have any login screen :confused:
Go System &#8594; Administration &#8594; Login Screen and choose «Show the screen for choosing who will log in».

---

### Post by vratnica on 2010-03-26
Thanx :D

Well I only have looked up these options, but nothing changed, since only my default option appeared there...

But as I logged in, i didn't have my keyboard mess anymore:D

Thanx a lot to all of you!

---

### Post by floopy1962 on 2010-09-26
so i want US on every start but... BUT I DON'T HAVE ONE :confused:
all my standart input-methods are gone ?????? :(
on every start its come with "US 105-key keyboard (with windows keys)" and i can't change it, i can't remove it, i can't add other english (this is the only one i have) and my arrows doesn't work... becouse there is no left and right arrows in this method :confused: 
[IMG]http://i52.tinypic.com/2s804tv.png[/IMG]
i live in bulgaria and i usuali use usa and bgr (bulgarian traditional phonetic) now i can't use other except "US 105-key keyboard (with windows keys)" so pls help how can i add,remove input-methods i tryed to upgrade the whole system now i'm with maverick and this doesn't help

ok i solve tha half of the problem... i just delete the "/usr/share/xmodmap/" folder and the keyboard working ok now :P
but now i got little problem again :(
i'm from bulgarian and now i don't have bulgarian... i don't have any langs 
can i download from somewhere keymaps...

---

### Post by TomaszC on 2010-10-23
Same annoying bug with a fresh 10.10 installation.

After reboot, keyboard ayout reverts to US, although I don't want to use this layout, remove it, set a different layout as default etc.

---

### Post by mjkuwp on 2010-10-27
I have a similar problem.  I need a US keyboard setting but i accidentally selected Romanian when I did the installation.

I know where to "Add..." and change the keyboard and I also know about the button 'apply system wide' but the computer is still reverting.  It also seems inconsistent but of course being a computer it probably is just a pattern that I have realized.

any further help out there?

My computer is a dual boot with VISTA, Dell inspiron 1525.

---

### Post by mjkuwp on 2010-10-28
I still have this problem.  I have been through the process of resetting back to the US keyboard several times now.  I've also searched and found comments about issues like this dating back at least to version 8 of Ubuntu.... I sure wonder why this has not been solved by now or why I cannot find a workaround

any help?  I have let Ubuntu run the 'updates'

---

### Post by mbrochh on 2010-11-09
Same problem here on Ubuntu 10.10
Annoying like hell. Also at the login I cannot chose any keyboard layout...

---

### Post by chweyd on 2010-11-13
If the keyboard layout reverts from e.g. LA to for example USA after every reboot, then you most probably use AutoLogon. To disable the wrong keyboard layout first disable AutLogon and logout. On the Login screen select your user-id, when the password field appears you will see on the lower part of the screen some listboxes from where you can select your layout. Select your non USA layout and login. Then you can activate AutoLogin again and the problem should be solved.

---

### Post by sthrudel on 2010-11-18
This worked for me:

```
sudo dpkg-reconfigure console-setup
```

---

### Post by DustWolf on 2010-12-11
Same problem, reported bug:
[https://bugs.launchpad.net/indicator-applet/+bug/688936](https://bugs.launchpad.net/indicator-applet/+bug/688936)

---

### Post by gmutlu on 2010-12-13
Still same bug here!
My workaround is to add the following line in ~/.bash_rc to set it to Turkish(tr)
"gconftool-2 --type list --list-type string --set /desktop/gnome/peripherals/keyboard/kbd/layouts [tr]"

---

### Post by Anoria on 2011-01-01
This bug was driving me crazy, with one US layout reverting to the one I (ill-advisedly) set when I installed Ubuntu. Fortunately, logging out and then selecting my account to log back in with gave me the options at the bottom of the screen that were mentioned in this thread, and I successfully changed to my preferred keyboard layout and it stuck when I logged back in. It's good to have some terminal commands for future reference, too. 
Thanks **c.j.stephen **and **chweyd**!

---

### Post by ItalOz on 2011-03-05
Thanks chweyd this worked for me

> **chweyd said:**
> On the Login screen select your user-id, when the password field appears you will see on the lower part of the screen some listboxes from where you can select your layout. Select your non USA layout and login.

even if I did not have autologin,
it took a couple of reboots for the system to understand

(Ubuntu 10.10 64b)

---

### Post by pauljwells on 2011-04-12
I think what you all really want is this:

[http://ubuntuforums.org/showpost.php?p=10668853&postcount=2]("http://ubuntuforums.org/showpost.php?p=10668853&postcount=2")

---

### Post by lordcx on 2011-05-17
Thank you [c.j.stephen]("http://ubuntuforums.org/member.php?u=1042498"), It works for me.

---

### Post by Alokin on 2011-07-06
Yes! I had the same problem. Keyboard reverting from manually set Croatian layout to USA on each reboot, even if USA deleted under System>Preferences>Keyboard etc. 
This solved my problem, I just changed USA to Croatian at the login screen, and now works fine!

Thank You!

---

### Post by jtarin on 2011-07-06
> **JamesParnell said:**
> I live in the UK, and have the default UK keyboard, with the layout as US on ubuntu, so I changed it to UK, deleted the US one, applied System-wide. which was fine until it rebooted, then it went right back to US...why is that?...and how can i fix it?You have downloaded the "Patriotic Ubuntu" please stand and salute when booting.....only if your a US citizen. All others please observe a moment of silence.

---

### Post by James Haigh on 2011-08-17
This is a known bug. The keyboard layout preference in the GDM login screen (which often goes unnoticed) doesn't sync with the keyboard layout preference in Gnome.

So check the keyboard layout preference at the bottom of the login screen.

Please see:
[https://bugs.launchpad.net/bugs/591895](https://bugs.launchpad.net/bugs/591895)

If you have this problem click 'Yes, it affects me'.

James.

---

### Post by James Haigh on 2011-08-18
> **Kixtosh said:**
> I have been using two keyboard layouts since Karmic Koala (was that 9.04?). ...

No, that's Jaunty Jackalope. Karmic Koala is 9.10. See: [https://wiki.ubuntu.com/DevelopmentCodeNames](https://wiki.ubuntu.com/DevelopmentCodeNames)

(In case you're wondering, I got your deleted post by email.)

---

### Post by tomsteemson on 2011-10-03
> **pauljwells said:**
> I think what you all really want is this:

[http://ubuntuforums.org/showpost.php?p=10668853&postcount=2]("http://ubuntuforums.org/showpost.php?p=10668853&postcount=2")

Thanks for that, Paul.  It was driving me nuts too. :KS

---

