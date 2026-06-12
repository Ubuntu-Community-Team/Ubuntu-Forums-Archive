---
title: "Creating a config file for a package"
date: 2008-12-20
forum: New to Ubuntu
---

### Post by Zerocool947 on 2008-12-20
So I downloaded a package for my laptop Utilities. I'm having trouble making it work. It looks like it didn't come with the files to actually run it >_<.

In the readme, it has this paragraph with general instructions as to how to run it.

"This program can be used by normal users or started as daemon by an init
script. Under Debian GNU/Linux it is possible to start automatically the
daemon at boot by creating an /etc/i8kbuttons configfile and setting the
I8KBUTTONS_UP_CMD, I8KBUTTONS_DOWN_CMD and I8KBUTTONS_MUTE_CMD variables
with the command which must be executed by the program.

Note the the /etc/i8kbuttons configfile is not installed by the i8kutils
package because the program is usually run by normal users. If you want to
use it as daemon you must create the config file yourself."

Could someone instruct me exactly as to how to do this? Thanks!

---

### Post by snova on 2008-12-20
Are you sure the program isn't in the repositories?

Would save a lot of trouble...

Edit: If this is i8kutils (it looks like it), it is, and you'd be better off installing through Synaptic.

---

### Post by Zerocool947 on 2008-12-20
That it is! I got it through Synaptic, how would I install it through synaptic?

Edit1:

Synaptic says it is installed. However, nothing runs, which is why I looked through the readme. Did I do something wrong?

---

### Post by Zerocool947 on 2008-12-20
Bump

---

### Post by snova on 2008-12-20
> **Zerocool947 said:**
> Bump

It's only been a half hour. ;) We know this forum moves quickly, but in general, wait at least a day.

What do you mean, "nothing runs"? They don't do anything? Or go out with an error of some kind?

---

### Post by Zerocool947 on 2008-12-20
Sorry, I'm used to quick forums haha.

Well, I don't care about the fans too much right now, the priority is getting the volume controls.

Basically, when I press the volume buttons on my laptop, the volume should go up, down or mute.

This utility should allow that, but it doesn't come with the files that will actually run the utility, per my understanding.

I'm not familiar with syntax enough to write these files, so basically I need some step by step instructions.

Edit:

I just tried putting their example file into the /etc/ folder. It didn't work.

---

### Post by snova on 2008-12-20
Hmm, it might not have anything to do with this package at all. Mine work just fine without it...

Can Gnome recognize these keys? That is, can you bind an action to them and have it work? That was my situation... I believe the problem was that they were acting on the wrong channel.

---

### Post by Zerocool947 on 2008-12-20
I don't know if Gnome can recognize the keys. How would I check something like that? And how would I fix it?

---

### Post by snova on 2008-12-20
System -> Preferences -> Keyboard Shortcuts

If you can bind one of the actions to one of your keys, they're recognized.

They might even work right...

---

### Post by Zerocool947 on 2008-12-20
Looks like Gnome can recognize the buttons. The thing is, I don't know my mixer commands.

In the sample file, there is this:

I8KBUTTONS_UP_CMD="echo up"
I8KBUTTONS_DOWN_CMD="echo down"
I8KBUTTONS_MUTE_CMD="echo mute"

Also, my sound channels are this:

Main
PCM
Front

---

### Post by snova on 2008-12-20
I don't know the command either...

I probably should have asked this much earlier, but do you even know that your keys won't function correctly from Gnome's built in shortcuts?

Have you tried avoiding all of this i8kutils mess and setting the necessary keys to Mute/Up/Down in System -> Preferences -> Keyboard Shortcuts, under Sound?

Just checking... some problems have surprisingly simple solutions... but I don't know whether you've tried that yet.

---

### Post by Zerocool947 on 2008-12-20
The keys are bound, and when I hit the button, a graphical volume bar comes up. However, it has no effect on the sound.

---

### Post by Zerocool947 on 2008-12-21
Bump for the morning crowd.

---

