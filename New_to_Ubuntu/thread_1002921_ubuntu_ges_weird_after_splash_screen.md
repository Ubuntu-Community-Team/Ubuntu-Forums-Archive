---
title: "ubuntu ges weird after splash screen"
date: 2008-12-05
forum: New to Ubuntu
---

### Post by topleftweb on 2008-12-05
Hi guys

finally took my first steps into linux a few weeks ago and installed ubuntu on one of my laptops.

worked great until last night, I restarted the laptop through the ubuntu GUI and something funky happened.

when it boots up, it gets as far as the ubuntu splash screen with the loading bar underneath, that bar fills up. But from there it just displays a weird gray and black pattern looking thing (looks like an old school tv w/ bad reception or something)

explaining this the best I can. like I say I'm new to this but can follow instructions if you can give me any clues how to get back in action :)

using Intrepid Ibex if that helps

---

### Post by Michael.Godawski on 2008-12-05
So every time you boot your machine you get this "TV-screen"?
Are you able to boot the Live CD?
Did you installed any updates before the "crash"?
Have you played with the graphical stuff like graphic drivers or Compiz?

---

### Post by topleftweb on 2008-12-05
Hello Michael

Yes it does this every time I boot

Booting from the CD gives same result

Have installed all updates pushed to me

The only additional software I have installed is Samba

Have not changed any graphics settings or drivers or Compiz

---

### Post by Michael.Godawski on 2008-12-05
Try this although is is a wild guess:

During the booting process hit ESC to get into the Grub boot menu thing.
See here how:

[LIST]
[*][https://help.ubuntu.com/community/BootOptions#Change%20Boot%20Options%20Temporarily%20For%20An%20Existing%20Installation](https://help.ubuntu.com/community/BootOptions#Change%20Boot%20Options%20Temporarily%20For%20An%20Existing%20Installation)
[/LIST]
follow the instructions there to add these additional boot options to your current kernel:

```
noacpi 
```
Reboot. Any difference?

---

### Post by topleftweb on 2008-12-05
Michael

Thank you for the suggestion.

I followed the instructions and rebooted.

No difference upon rebooting.

---

### Post by damis648 on 2008-12-05
Try adding
```
noapic nolapic acpi=off
``` in the same method. Any difference?

---

### Post by topleftweb on 2008-12-05
hello damis648

I added the stuff you suggested.

No difference after reboot.

Really appreciate you guys bothering with this btw.

---

### Post by caljohnsmith on 2008-12-05
> **topleftweb said:**
> Hello Michael

Yes it does this every time I boot
[COLOR="Blue"]
Booting from the CD gives same result[/COLOR]

Were you previously able to boot the Ubuntu CD OK? If so, then it sounds like you might have a hardware problem if you get the same strange booting behavior from both the Live CD and your Ubuntu install.

---

### Post by topleftweb on 2008-12-05
Hello caljohnsmith

This was the first occasion that I have had to boot from the Ubuntu CD since the original install.

Aside from that I don't have any information about the success of booting from the CD.

---

### Post by caljohnsmith on 2008-12-05
So is it safe to assume you were able to boot the Ubuntu Live CD OK a few weeks ago in order to install Ubuntu? If that's true, again it sounds like you could be having hardware issues. Do you have any other Live CDs you can boot? If not, I would try downloading another distro like Mandriva, PCLinuxOS, Knoppix, OpenSUSE, etc and see if you get similar results. That will give an important clue whether you could be having a hardware problem or not. Also, do you happen to have Windows installed on that computer? If so, how about booting it and see what happens. Let me know how it goes. :)

---

### Post by topleftweb on 2008-12-05
Ok yes I was able to boot the Ubuntu Live CD OK a few weeks ago in order to install Ubuntu.

I do not have windows installed on the machine in question.

I'll try your suggestions, starting with a different Live CD, and if I get the same result, trying another distro to see if I get similar results.

Very supportive group you have here, thanks so much for helping me troubleshoot this.

I'll report back to let you know how it goes :)

---

