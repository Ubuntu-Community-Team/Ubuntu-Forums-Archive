---
title: "firefox unstable"
date: 2009-04-26
forum: New to Ubuntu
---

### Post by jtmedin on 2009-04-26
I have been unable to keep firefox running for more than a couple of minutes. It just crashes & disappears. Where do i begin? Running 3.0.9 TIA

---

### Post by Happy_Man on 2009-04-26
You should begin by disabling all your extensions and seeing if that fixes it. This way, we'll know if it's an extension problem or a Firefox problem.

---

### Post by |Mitch| on 2009-04-26
As Happy_Man said, Did the stability issues start happening just recently?

---

### Post by jtmedin on 2009-04-26
Last few days perhaps less than a week. How do u disable extensions? TIA

---

### Post by |Mitch| on 2009-04-26
Tools/Add-ons on the Firefox menu

---

### Post by jtmedin on 2009-04-26
Evidently i only have 2 extensions: ubuntu firefox mod 0.6 & wx bug. Both are now disabled. We shall see :-) Crashed trying to send this.

---

### Post by whatep on 2009-04-27
I have the same problem. I have disabled 20 extensions ( I can list them if that would help) but Firefox is still crashing. Please let me know if there is more information I can extract that would help track this down.

---

### Post by whatep on 2009-04-27
I think this is a problem with Flash (at least as far as I was concerned). I followed the instructions in these forums at: 

[http://ubuntuforums.org/showthread.php?t=1137803&highlight=firefox](http://ubuntuforums.org/showthread.php?t=1137803&highlight=firefox)

and the problem went away.

Hope this works for you too.

---

### Post by jtmedin on 2009-04-28
tried the rm flash drive ... but still unstable :(

---

### Post by Crafty Kisses on 2009-04-28
What are your system specs? Try using like SwiftFox or something.

---

### Post by Seq on 2009-04-28
Run firefox (either from the terminal or ALT+F2) with the -P option.

```
firefox -P
```

Then create a new profile (name it anything). See if you have problems with this new profile.

Also, firefox has a "safe mode" that disables extensions and plugins. I'm unsure of the switch to activate it offhand (and I don't have access to a Linux machine with X installed right at the moment) but you can probably find it with 'firefox --help'

EDIT: Your old profile is accessible by running 'firefox -P' again to switch back. Anything installed system-wide will still affect the new profile, but shouldn't affect safe-mode.

---

### Post by DustyMP on 2009-04-28
Just an idea, start synaptic by going to system -> administration -> synaptic package manager and enter your password. Click on Edit menu and select Fix broken packages. If something went awry in the install that should take care of it.

---

### Post by jtmedin on 2009-04-28
I downloaded firefox 3.5b4 & am running that. Will see how that goes. How does one install 3.5b4? I downloaded it to a folder & then clicked on firefox file which got 3.5b4 running but am unsure how to replace 3.0.9. BTW what is surefox? TIA

---

### Post by jtmedin on 2009-04-28
> **Codename said:**
> What are your system specs? Try using like SwiftFox or something.

Runing 9.04 what is swiftfox? TIA

---

### Post by zeex on 2009-04-28
Start using Epiphany. 

Much better than firefox. I've already dumped firefox. Epiphany is awesome.

---

### Post by sports fan Matt on 2009-04-28
I thought the Swiftfox project was no longer being developed.

---

### Post by Crafty Kisses on 2009-04-28
Not sure, but the site is still up and running, they have the latest version at like 3.1 or something like that. [http://getswiftfox.com/](http://getswiftfox.com/)

---

### Post by jtmedin on 2009-04-30
Since the update for 3.0.10 came out ff has been stable :P

---

