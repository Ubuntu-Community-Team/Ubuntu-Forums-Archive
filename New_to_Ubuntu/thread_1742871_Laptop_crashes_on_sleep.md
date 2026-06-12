---
title: "Laptop crashes on sleep"
date: 2011-04-29
forum: New to Ubuntu
---

### Post by Alan5 on 2011-04-29
I am testing Ubuntu 10.10 booting from CD prior to adoption on an Acer 5735Z laptop. Generally this is going well.

For my latest run  :

I did not adopt my locale keyboard, which is UK English. I do not think this to be significant. The effect from default should be limited to printable characters.

I ran the machine test.

I pressed Fn+F4 = Zz and the screen went black to show :

(process:358: GLib-warning **: getpwuid_r(): failed due to unknown user id (0)
    speech despatcher disabled: edit /etc/default/speech-despatcher
* PulseAudio configured for per-user sessions
saned disabled: edit /etc/default/saned
* Enabling additional executable binary formats binfmt-support                    [ OK ]
* Checking battery state...                                                                             [ OK ]

The fan continued running.

No user action produced a response, except pressing the button to open the CD/DVD drive released the tray.

I pressed every button and key and ctrl+alt+del . All had no effect.

I removed the power supply and let the machine expire. As the boot was from CD there was no improper shutdown.

I wish to adopt ubuntu, but not if there is a risk of this. I would appreciate advice.

My thanks.

---

### Post by Alan5 on 2011-04-29
I have done more work.

Allowing the machine to sleep on time out behaves perfectly.

Setting the keyboard to UK and keying to sleep behaves perfectly.

Problem solved.

---

