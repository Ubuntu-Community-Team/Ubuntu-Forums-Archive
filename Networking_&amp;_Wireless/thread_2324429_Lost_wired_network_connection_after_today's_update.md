---
title: "Lost wired network connection after today's updates"
date: 2016-05-13
forum: Networking &amp; Wireless
---

### Post by Randy M on 2016-05-13
My wife's machine is running Xubuntu 14.04 and, after today's updates, cannot connect to the network. I don't know what was updated, but it appears that there are no network connections. I tried adding one, but all of the fields are greyed out and can't be edited. Any guesses on what happened and how to fix it?

[http://i.imgur.com/o9PGyuY.jpg](http://i.imgur.com/o9PGyuY.jpg)

---

### Post by Bashing-om on 2016-05-13
Randy M; Yikes !

See if you are the victim of this update bug:
[https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/1539634](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/1539634)

If so .. try and download:
[https://launchpad.net/ubuntu/+source/network-manager/0.9.8.8-0ubuntu7.3](https://launchpad.net/ubuntu/+source/network-manager/0.9.8.8-0ubuntu7.3)
on a different machine, transfer the file to the broke system and install the new network-manager package.

[INDENT][INDENT]been there
[INDENT][INDENT][INDENT]seen that
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by lesliek2 on 2016-05-13
I installed the new network-manager package, but now the booting up process stalls and I can't get to my desktop. I have no idea how to go about solving the problem and need my computer. Can anyone please give me some idea as to what to do?

---

### Post by sam_baker2 on 2016-05-13
Randy M, I have xubuntu 1404 LTS, and after updating today, had the same problem.
Had to re-install the network-manager that the update changed.
See my recent post:
[http://ubuntuforums.org/showthread.php?t=2324421](http://ubuntuforums.org/showthread.php?t=2324421)

---

### Post by watchpocket on 2016-05-13
I am also suddenly today a victim of this update.  

Unbelievable that this sort of thing can still happen.  That an update can just completely hose network connectivity like this is very bad.

This happened a few months ago from one of the proposed updates, and I specifically stopped allowing the proposed or experimental updates to come in, specifically to avoid this.  

In any event I'll try to apply the fix, ***thank you*** for posting it.

---

### Post by Bashing-om on 2016-05-13
et all ; Hey !

I have also run across this fix:
[http://askubuntu.com/questions/771627/14-04-network-manager-stopped-working/771841#771841](http://askubuntu.com/questions/771627/14-04-network-manager-stopped-working/771841#771841)
posted here by another forum user .
Might be an easier method to apply .

[INDENT][INDENT]'buntu
[INDENT][INDENT][INDENT]more than one path to an end
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by Randy M on 2016-05-13
> **Bashing-om said:**
> Randy M; Yikes !

See if you are the victim of this update bug:
[https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/1539634](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/1539634)

If so .. try and download:
[https://launchpad.net/ubuntu/+source/network-manager/0.9.8.8-0ubuntu7.3](https://launchpad.net/ubuntu/+source/network-manager/0.9.8.8-0ubuntu7.3)
on a different machine, transfer the file to the broke system and install the new network-manager package.
[INDENT][INDENT]been there[INDENT][INDENT][INDENT]seen that
[/INDENT]
[/INDENT]
[/INDENT]
[/INDENT]
[/INDENT]


Thanks, I'll dig into how to install the TAR packages. I'm more of a user than a tinkerer.

---

### Post by Bashing-om on 2016-05-13
Randy M; Welll ....

You may find the "recovery mode" method easier to implement .

[INDENT][INDENT]different strokes
[INDENT][INDENT][INDENT]for different folks
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by Randy M on 2016-05-13
> **Bashing-om said:**
> Randy M; Welll ....

You may find the "recovery mode" method easier to implement .
[INDENT][INDENT]different strokes[INDENT][INDENT][INDENT]for different folks
/INDENT][/INDENT]
[/INDENT]
[/INDENT]
[/INDENT]


You, sir, are a prince among men. The recovery mode did the trick once I found out how to get to the GRUB menu. For those finding this thread, Shift doesn't work, but ESC does. Many thanks for the help.

---

### Post by Bashing-om on 2016-05-13
Randy M; Great !

You wandered around, and see what happened . :)

with the EFI firmware , yeah, it is the escape key that grub recognizes .

[INDENT][INDENT]together
[INDENT][INDENT]we can
[/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by watchpocket on 2016-05-13
Yes indeed -- the recovery method to fix / upgrade Network Manager totally worked, and it's a very easy  (idiot-proof, in fact) fix to implement.

(Of course, everything's easy once you know what to do.)

Jit's explanation and screenshots were a model of clarity.

Thank you so much for pointing to that, Bashing-Om.

---

### Post by jso28972 on 2016-05-14
Nothing that has been posted here helps me - the solutions don't work. Is there any body at canonical who is taking any responsibility for getting a fix out on this?
I've stuck with ubuntu for a long time - but I'm getting tired of amateur hour.

---

### Post by jso28972 on 2016-05-14
> **jso28972 said:**
> Nothing that has been posted here helps me - the solutions don't work. Is there any body at canonical who is taking any responsibility for getting a fix out on this?
I've stuck with ubuntu for a long time - but I'm getting tired of amateur hour.

Solution for people having trouble with instructions provided - try installing debs one at a time, manually - that cracked it for me.
I sure would like to find a way to get some support direct from canonical, as a home user. I actually wouldn't mind paying some modest fee. The folks here at the forums are terrific - but "a bunch of helpful, well-intentioned guys" is not a support system. 
Maybe I am ahead of myself - IS there actually a paid support tier available to the home user? If it was reasonable, I'd likely go for it.:confused:

---

### Post by wildmanne39 on 2016-05-14
Please use thumbnails or Url's when posting images because many people have slow internet connections and loading pages with large images is very difficult for them.

---

### Post by watchpocket on 2016-05-15
If you haven't yet tried the method posted here:

[http://askubuntu.com/questions/771627/14-04-network-manager-stopped-working/771841#771841](http://askubuntu.com/questions/771627/14-04-network-manager-stopped-working/771841#771841)

you should, it worked for me to get Network Manager working again.  It's a very clear, step-by-step explanation with screen shots.

---

### Post by C2i18zSar7 on 2016-05-15
well then, this also totally screwed my laptop... i only have wlan0 so the recovery option doesn't work, installing the debs manually lets network manager run again but it can't find any wifi networks :(

I would class this as a pretty major bug...ya know completely disabling the network &#128514; especially seeing as the bug was reported 3 months ago on the proposed repository!

---

### Post by kithrup on 2016-05-15
> **Bashing-om said:**
> et all ; Hey !

I have also run across this fix:
[http://askubuntu.com/questions/771627/14-04-network-manager-stopped-working/771841#771841](http://askubuntu.com/questions/771627/14-04-network-manager-stopped-working/771841#771841)
posted here by another forum user .
Might be an easier method to apply .[INDENT][INDENT]'buntu[INDENT][INDENT][INDENT]more than one path to an end
[/INDENT]
[/INDENT]
[/INDENT]
[/INDENT]
[/INDENT]


That did it, thank you very much indeed, folks, great forum.

I would like to add that someone suggested elsewhere it was our fault for enabling trusty-proposed updates. <<<< THIS IS NOT TRUE in my case, and, I suspect, in many others' as well. (I will respectfully decline to link as I'm sure those who experienced and solved the problem discovered on their own)

---

### Post by wildmanne39 on 2016-05-15
> **p3t3.abroad said:**
> well then, this also totally screwed my laptop... i only have wlan0 so the recovery option doesn't work, installing the debs manually lets network manager run again but it can't find any wifi networks :(

I would class this as a pretty major bug...ya know completely disabling the network &#128514; especially seeing as the bug was reported 3 months ago on the proposed repository!
Please start your own thread and post the results of the wireless script in my signature in code tags and I will take a look.
Thanks

---

