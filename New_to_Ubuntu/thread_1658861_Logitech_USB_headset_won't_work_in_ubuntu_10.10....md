---
title: "Logitech USB headset won't work in ubuntu 10.10... help?"
date: 2011-01-03
forum: New to Ubuntu
---

### Post by welwitschia on 2011-01-03
I am a week-old newbie to Ubuntu. 

Here's what I tried:
1. Put logitech USB headset in USB-port.
2. Opened sound preferences.
3. Headset was recognised in "Hardware", "Input" and "Output" so I selected it.
4. Closed sound preferences.
5. Opened sound preferences again and it had re-selected internal audio of my laptop.

Why? How can I save the headset settings? It works, but won't "stick".

Please help, there's probably a really simple answer that I just don't get.

---

### Post by vivek.pandey on 2011-01-03
> **welwitschia said:**
> I am a week-old newbie to Ubuntu. 

Here's what I tried:
1. Put logitech USB headset in USB-port.
2. Opened sound preferences.
3. Headset was recognised in "Hardware", "Input" and "Output" so I selected it.
4. Closed sound preferences.
5. Opened sound preferences again and it had re-selected internal audio of my laptop.

Why? How can I save the headset settings? It works, but won't "stick".

Please help, there's probably a really simple answer that I just don't get.

try this once n check whether its working 4 u or not
go to sound prefernces->outpit->connecors->analog headphones

---

### Post by welwitschia on 2011-01-03
Thanks for your answer. The only two options I have are:

1. sound preferences->output->connectors->analog output
2. sound preferences->output->connectors->analog speakers

However it doesn't matter which one I choose, because as soon as I close the sound preferences window and re-open it, everything has gone back to how it was (i.e. headset not being used even though it is both detected and works, while sound preferences are open).

More help? Is there anyone experiencing the same problem?

---

### Post by khelben1979 on 2011-01-03
Have you tried to boot the system when the headset is connected? 

On Debian, in doing so can make the headset take over the whole sound system. Works with the Sennheiser headset (inbuilt sound chip), so I don't know about the one you got. Once connected, close down the web browser for instance and then start it again, it makes the web browser use the headset instead of the sound from the sound- card/chip.

Exact what is the model of the USB headset?

---

### Post by welwitschia on 2011-01-04
Thanks for your advice.

In fact, I don't know what it was that worked, but I first re-did the OS to 10.04, because the headset worked there earlier. Also I connected it before turning on the computer - might have also helped, like you suggested. I'll try to work it with 10.10 somewhere in the distant future, but right now I just need it to work.

In any case I now have a fully functional headset - X-lite combination. Thanks!

---

### Post by ejwkamstra on 2011-02-10
Ok. Here is what I did.

Open a terminal and type 'alsamixer' (without the quotes). Than press 'F6'. It will open a small windows. Go with the cursors to your headset and 'ENTER'. Now you can use the cursor 'up' to get the volume up and the headset working. When you also want the mic go up, than first cursor 'right' and than 'up'. 'esc' is getting you out of here and saves this for this session.

Hope I helped someone with this :D

ejwkamstra

---

### Post by CyDharttha on 2011-04-29
I have the same problem. Headset was fine in Ubuntu 10.04; upgraded to 10.10 a few days ago, and now found that headset output can't be selected in the Output tab. Shows up in Hardware tab, but no input or output item to select in those tabs.

I started looking at [https://help.ubuntu.com/community/SoundTroubleshootingProcedure](https://help.ubuntu.com/community/SoundTroubleshootingProcedure) and ran:

```
aplay -D plughw:2,0 /usr/share/sounds/alsa/Front_Center.wav
```

which played a sound to the headphones just fine.

I don't have anything else on it right now, except to add my experience.

Thanks all!

---

### Post by scott-ian on 2011-04-29
From what I can tell, this problem does not have anything to do with the specific device.  I suspect it is a problem with all audio over USB, but I might be wrong.

---

### Post by metallus on 2012-04-04
```
sudo pkill -9 pulseaudio
service pulseaudio restart
```NOTE that the second command is NOT run with super-user access. you should run it with your user.

---

