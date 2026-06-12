---
title: "Custom keyboard shortcuts - implementing KEYSTROKE combinations?"
date: 2010-06-12
forum: New to Ubuntu
---

### Post by phubert28 on 2010-06-12
I have a Logitech Illuminated Keyboard that, under Windows using Logitech's SetPoint software, can configure the function keys to KEYSTROKE combinations.

Under WinXP I was using F1-f9 for underline, italics, bold, copy, paste, cut, shift-delete, and copy all.

Is there any way to create CUSTOM commands that would effect these actions under the Keyboard Shortcuts - Custom????

I see I need to bind a COMMAND to the key.
Could those keystrokes combinations (including, perhaps, Ctrl-A, Ctrl-C, together) be implemented in a shell script and THEN bound to the key as a shortcut???

My ORIGINAL thought was to find some way to re-map the keybaord, itself.
It would be a great advantage if I could do this!!

(I have lobbied Logitech to PROVIDE SetPoint for mouse and keyboard under Ubuntu and will likely continue to do so - I encourage everyone else to do the same wherever a vendor provides functions under Windows that aren't available under Linux - another example is the Dymo 400/450 turbo - twin turbo label printers and the Dymo address book (with online address correction software) software.

---

### Post by Ollytheninja on 2010-10-03
Hi there,
I know this is a little old and you have probably found an answer elsewhere on the interwebs, but I was looking for something similar and found this thread so is it possible for you to tell us how you fixed it(if you did)?

[This is a tutorial that i found quite useful but still didn't answer my questions.]("http://www.howtogeek.com/howto/ubuntu/assign-custom-shortcut-keys-on-ubuntu-linux/")

---

### Post by phubert28 on 2010-10-03
[Ollytheninja]("http://ubuntuforums.org/member.php?u=1096436"),

I tried just that and it simply didn't work for ME, either.

I read recently that Canonical is trying to get hardware manufacturers to better support Ubuntu and I'm afraid this is likely the ONLY solution for MY needs.

But I AM patient.

I have Windows XP SP3 installed under Oracle's (formerly Sun's) VirtualBox, and HAVE gotten my Dymo software running under it and recognizing my Dymo label printer. But beyond that I'm not using Windows at all.

AND, Windows under VBox doesn't recognize my Logitech devices AS what they are, so I can't configure them with the Logitech software - since it simply doesn't SEE its own devices.

I hope to convert at least ONE friend to Ubuntu - getting him COMPLETELY off Windows 7. If more of us do this, the hardware manufacturers will HAVE to come along!

---

### Post by mastermindg on 2010-12-07
In Gnome you can use Gnome Configuration Editor (gconf-editor) to create custom keyboard shortcuts. I've setup my function keys to open up my favorite apps. I had to change the shortcut for Eject since XF86Eject isn't working by default.

For system-wide changes (not in Gnome) check out this post:

[https://wiki.ubuntu.com/X/Config/Input]("https://wiki.ubuntu.com/X/Config/Input")

---

