---
title: "weird letters in terminal, Virus in ubuntu?"
date: 2010-04-29
forum: New to Ubuntu
---

### Post by nightwolf2k5 on 2010-04-29
Hi there,

I had suggested Ubuntu to my friend as the ultimate OS to save himself from viruses. He used it for a while and now seems to have a very strange issue.
After about 5 minutes of logging into his machine, it suddenly acts up like somebody is pressing the right button!
If we select a document/folder while using Nautilus, the highlighted folder keeps changing (exactly like what would happen if somebody was pressing the right key!)

Now here is where it gets weird, when using terminal, we continuously get the characters ```
[[C^[[C^[[C^
```
He also mentioned that he faces this problem while booting into ubuntu as well.

Can this be a virus?! If not, what is it? We checked the hardware, and he went as far as removing the right key from the keyboard of his laptop. So I guess we can rule out a hardware issue.

Edit: He is using Ubuntu 9.04

---

### Post by raydeen on 2010-04-29
Removing the key and having the problem persist doesn't necessarily mean that the hardware is good. There could be a short in the contact for that key or there might be something wrong with the ribbon connector from the keyboard to the motherboard, or the keyboard itself may have gone bad. Depending on his machine, it may be a simple fix to replace the keyboard. The way to really test it would be to open up the laptop enough to detach the built in keyboard and then attach an external keyboard and see if the problem persists. He didn't spill anything into his laptop did he? I've seen some people freak out that they had a virus only to find they got a bit sloppy with their coffee that morning. :)

---

### Post by nightwolf2k5 on 2010-04-29
Ok, to rule out the hardware issue, here is something:
The behaviour is non existant while using the firefox or gedit..

edit: scratch that.. it is also present in the browser.
Ok, I would buy the hardware issue if the terminal did not have those weird characters.. any ideas as to what might cause that?

---

### Post by P4man on 2010-04-29
check system > prefences > keyboards > layout > options

check if he didnt enable something there he didnt want to.  Also check mouse keys and accessibility (sticky keys). Make sure its all OFF.

---

### Post by arrrghhh on 2010-04-29
> **nightwolf2k5 said:**
> Ok, I would buy the hardware issue if the terminal did not have those weird characters.. any ideas as to what might cause that?

Same reason my friend.  If the keyboard is escaping some of the commands, or pressing down more than once button at once... I would definitely pull the ribbon cable on the keyboard and plug in an external one, there's no other way to isolate it really.

---

### Post by M1ke on 2010-04-29
> **nightwolf2k5 said:**
> Ok, I would buy the hardware issue if the terminal did not have those weird characters.. any ideas as to what might cause that?

I've seen it a few times, the terminal simply doesn't recognise whatever input it's getting from the keyboard. If I use any arrow keys after hitting ctrl, alt & F1 I see the same characters.

Still sounding like a hardware fault to me.

---

### Post by thumper13 on 2010-04-29
```
[[C^[[C^[[C^
```

These are "escape codes" for the keyboard. See, when you press a key that isn't a letter, e.g. the right arrow key, the pc must recognize the key is being pressed. These codes are sent to the pc, and if it's a program that uses the right arrow key, such as a browser or a game, it moves the character right, or something along these lines. Since terminal has no use for arrow keys, it shows these so you know the key is being pressed. I'm a little rusty with escape codes, but the CTRL or ALT key could also be fubar'd.

My advice is to try a second keyboard hooked up a ps/2 slot, or usb. Then check in the bios for an option to disable the onboard keyboard. Some laptops you can disable it, some you cant. If you can't, just try booting it with a keyboard plugged in and see if the issue continues. 

Viruses in linux are rare, because to be honest, hackers are lazy. Why infect a piddly little 1% of computer users with a virus, when they can infect the other 95% with windows? However, if you believe there to be a virus, look into ClamAV, I recommend it.

---

### Post by sydbat on 2010-04-29
> **thumper13 said:**
> <snip>

Viruses in linux are rare, because to be honest, hackers are lazy. Why **go through all the trouble of having to make sure the user has to type in their password so one box might be infected** with a **specific piece of malware that will not go beyond the box it is installed on**, when they can infect windows **boxes simply by having the user click on something and have it spread like wildfire to everyone the user comes into contact with (via email, sharing files, etc, etc, etc)**? However, if you believe there to be a **Windows** virus **on a Windows partition attached to your Ubuntu install**, look into ClamAV, I recommend it.There, fixed it for you...

---

### Post by nightwolf2k5 on 2010-04-29
I guess it really is a hardware issue.. my only regret is that my friend does not seem to think so.. he is convinced that it is a Ubuntu virus..
i guess he is all set to format it back to crapdoes...
I'll keep you guys posted in case it does not turn out to be a hardware issue..

---

### Post by rudy.elgato on 2010-04-29
do have a livecd?  try booting off of that and see what happens...

---

### Post by P4man on 2010-04-29
it could be a hardware issue, but honestly Im not convinced. either its one of those assistive technologies (like sticky keys) that are enabled by accident,  or it could be a problem with an input device. Ive seen this on a laptop that has a troublesome touchpad/mouse stick combo. I do get "lost synch" messages in my logs, so it could be worth having him check his dmesg logs.

Whatever it is, its not a virus.

---

### Post by lykwydchykyn on 2010-04-29
Why would someone write a virus that spit out escape codes to the terminal?

If someone were going to write a virus to infect Linux boxes, they'd have it do something useful like open a rooted ssh or send out spam.

At the very least, they'd make it do some wickedly cool ASCII art.  

```

 _________________
< U B0X B DEDDED1 >
 -----------------
        \   ^__^
         \  (xx)\_______
            (__)\       )\/\
             U  ||----w |
                ||     ||

```

---

### Post by arrrghhh on 2010-04-29
> **lykwydchykyn said:**
> At the very least, they'd make it do some wickedly cool ASCII art.  

```

 _________________
< U B0X B DEDDED1 >
 -----------------
        \   ^__^
         \  (xx)\_______
            (__)\       )\/\
             U  ||----w |
                ||     ||

```

*Starts writing a Linux virus that does wicked cool ASCII art*

That's f-in awesome.

---

