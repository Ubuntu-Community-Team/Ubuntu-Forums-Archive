---
title: "Toshiba Equium A100-306: Fnfxd - My Hotkey functions won't work."
date: 2009-07-15
forum: New to Ubuntu
---

### Post by Siobhan on 2009-07-15
Hi, hi.

_My details:_
Ubuntu Release 9.04 Jaunty
Kernel Linux2.6.28-13-generic
Gnome 2.26.1
Toshiba Equium A100-306
Intel Core2 CPU
Machine Hardware Name: i686 ([COLOR=SeaGreen]$*uname -m*[/COLOR])

And uh... I can't think of anything else that may be useful.

_Zee lowdown:_
After some looking around the internet I found that fnfx is the program I needed soooo I installed the fnfxd and fnfx-client packages from the repositories.

When I type [COLOR=SeaGreen]$*fnfx-client*[/COLOR]
I get this error
[COLOR=RoyalBlue]fatal error: Could not open "/home/siobhan/.fnfxrc". Please make sure that the default config is accessible.[/COLOR]

When I type [COLOR=SeaGreen]$*sudo fnfxd*[/COLOR]
I get this error
[COLOR=RoyalBlue]fatal error: Could not open /proc/acpi/toshiba/keys.
Please make sure that your kernel has enabled the Toshiba option in the ACPI section.
For more information read the documentation and/or [http://fnfx.sf.net/index.php?section=doc#kernel](http://fnfx.sf.net/index.php?section=doc#kernel).[/COLOR]

Of course I followed the link but the website doesn't seem to be working. All I can read is the news/home page no matter what I click on...

The directory [COLOR=DarkRed]/proc/acpi/toshiba[/COLOR] doesn't exist (I checked). Why the hell not! I wish I knew. D:

Anyways, I then decided to see could I locate the [COLOR=DarkOrchid].fnfxrc[/COLOR] file using the locate command but nothing. And then for pig iron I decided to search for anything with fnfx in it but nothing happened. And I know for certain there's a file called[COLOR=DarkOrchid] fnfxd.conf[/COLOR] ([COLOR=DarkRed][COLOR=Black]in [/COLOR]/etc/fnfxd[/COLOR]) so then I got confused and wondered why locate wouldn't find it. There's a [COLOR=DarkOrchid]keymap[/COLOR] in the same directory so I tried the locate command and it brings up a list of other keymaps but not the one in the fnfxd directory... It's like it's an invisible or a ghost directory. :O!

Anyways, I decided it was time to ask for help!

Does Fnfx even work for my laptop? I read somewhere it doesn't work for Toshibas with Phoenix BIOS but I don't know what kind of BIOS I have or how to find out. >_>

I am quite the beginner but definitely willing to learn so share your knowledge please!!

Siobhán. =]

---

### Post by lisati on 2009-07-16
I used to have one of the Toshiba A100 range but never used the fn keys on it with Ubuntu, and I don't have it anymore, so I'm unable to confirm if it will work for you. I just had a look at the [web site]("http://fnfx.sourceforge.net/index.php?section=doc#kernel") - it seems to be up and running for me, but the most recent entry on the page I looked at seemd to be a few years ago.

---

### Post by Siobhan on 2009-07-16
Thanks for your reply. =]

I did some more looking around. My kernel doesn't have Toshiba support. I'm missing the [COLOR=DarkRed]/proc/acpi/toshiba [COLOR=Black]folder with zee files (as I said before) aaaand if I want it I'd have to look into patching the kernel or upgrading or something.
But I'd sooo much rather not getting into that at alll.[/COLOR]
[COLOR=Black]So I guess it's really a lost cause until I upgrade to a kernel *with* toshiba acpi support![/COLOR]
[COLOR=Black]-Sigh.-
[/COLOR][/COLOR]

---

### Post by AI52487963 on 2010-01-20
> **Siobhan said:**
> Thanks for your reply. =]

I did some more looking around. My kernel doesn't have Toshiba support. I'm missing the [COLOR=DarkRed]/proc/acpi/toshiba [COLOR=Black]folder with zee files (as I said before) aaaand if I want it I'd have to look into patching the kernel or upgrading or something.
But I'd sooo much rather not getting into that at alll.[/COLOR]
[COLOR=Black]So I guess it's really a lost cause until I upgrade to a kernel *with* toshiba acpi support![/COLOR]
[COLOR=Black]-Sigh.-
[/COLOR][/COLOR]

I'm in the same boat. Are there any updates to this?

---

### Post by Siobhan on 2010-01-21
Nay, I'm afraid.
I think it's the Pheonix BIOS that's the reason it doesn't work... I can't really remember. It's been a very long while since I thought about it. Living without Fn functions ain't so bad. For me anyways. :o =]

---

