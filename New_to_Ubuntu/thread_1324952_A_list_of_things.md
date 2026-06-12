---
title: "A list of things"
date: 2009-11-13
forum: New to Ubuntu
---

### Post by Sezotove on 2009-11-13
okay, my windows took a **** on me AGAIN today, so im pretty much done with it for now, and i have used linux a little before, but this time, heres a list of things that just dont seem right to me

1) my Ctrl+T will not open a new tab in firefox(its just annoying)
2) i have dual screens, one is a 32' HD tv, and the screen resoultion is either retarted or to big to where the windows resize buttons are not visible
3)When i restart, my tool bars ARE never on the screen there supposed to be, and i have made the screen that i need them on to be my main screen.
4) After about 6 hours of tinkering i have come to realise that i either have my sound working and not Mic, or nothing all together. This has got to be fixed. For some reason it just wont work what so ever

thanks for the help in advanced

---

### Post by jimmy the saint on 2009-11-13
1) Ctr-t works for me.  That is strange.
2) Do you have an nvidia card?  If so, you may want to use that configuration.  Dual monitors of different sizes are not handled well in gnome.  It is known and its a real pain in the ***.  Bug the gnome people about it, it should have been fixed a long time ago.  Maybe there is a good way now, but there wasn't when I was looking into it.  You can run dual x's, but you won't be able to drag between them.
3) If one is a vga hookup it will always be the primary, no matter what you pick.  I ran into that issue as well.
4)have you tried to mess with the inputs in alsamixer?

---

### Post by Sezotove on 2009-11-13
1) I know its wierd i think there might be conflicting with Compiz, i have got to check it and see.
2)I do have an Nvidia card, and i use it to configure, but it doesnt seem to work correctly. When i was using windows, there was an option to "Resize myHD TV" which worked. But its not on the linux version :(
3)Im using a DVI to VGA adapter for my small screen(the one i want to be my main because of the issue in #2) and a DVI to HDMI cable for the TV so it, idk just hates me i guess
4)I have, and nothing seems to work, and NOW i have found another problem, i had pulseaudio and when i installed skype it has set the sound devices to "pulseAudio server (local)" and doesnt give me any options, i have uninstalled skype and pulse audio but i guess when you uninstall something it doesnt get rid of the configuration.

---

### Post by jimmy the saint on 2009-11-20
If you want to get rid of the configuration you need to purge it.  In synaptic, select "completely remove" instead of remove

---

### Post by 3rdalbum on 2009-11-20
> **Sezotove said:**
> 
4)I have, and nothing seems to work, and NOW i have found another problem, i had pulseaudio and when i installed skype it has set the sound devices to "pulseAudio server (local)" and doesnt give me any options, i have uninstalled skype and pulse audio but i guess when you uninstall something it doesnt get rid of the configuration.

That's correct: When you are running Pulseaudio, you don't set up sound inputs and outputs from with Skype, you set them up from Pulseaudio. The little speaker icon on your panel; right-click it and choose Sound Preferences, and then set up your inputs and outputs from there.

---

