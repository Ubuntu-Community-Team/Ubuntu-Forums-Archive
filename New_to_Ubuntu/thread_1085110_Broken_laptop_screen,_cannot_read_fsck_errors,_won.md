---
title: "Broken laptop screen, cannot read fsck errors, won't boot"
date: 2009-03-02
forum: New to Ubuntu
---

### Post by El Lance-O on 2009-03-02
I already posted this in the hardware section, but I have lost my faith in this community as almost all of my posts are constantly ignored.

Is there any way to force the output to my external monitor so I can see what I am doing, or what I need to do?

This is a very dire situation, so please, just this one time, someone get back to me.

---

### Post by brian_p on 2009-03-02
> **El Lance-O said:**
> 

Is there any way to force the output to my external monitor so I can see what I am doing, or what I need to do?

A search with 'laptop external monitor' has the first hit as:

[http://www.computerhope.com/issues/ch000801.htm](http://www.computerhope.com/issues/ch000801.htm)

---

### Post by El Lance-O on 2009-03-02
Look, I know how an external monitor works.

YES, I have tried using the function key to switch the display. Does not work.

YES, I have tried starting GDM to get it to switch, GDM will not run for some reason I cannot identify as I cannot read any of the errors.

I'm talking about displaying the GRUB loading info and what not, EVERYTHING BEFORE GDM, to an external so I can read my fsck errors that I am getting that's keeping it from booting.

---

### Post by cariboo on 2009-03-02
You should be able to see what you are doing, before X starts up. 

What happens when you boot from the LiveCD?

Jim

---

### Post by Truefire on 2009-03-02
> **cariboo907 said:**
> You should be able to see what you are doing, before X starts up. 

What happens when you boot from the LiveCD?

Jim

Jim's got a point - the LiveCD should switch to it on boot if it is plugged in - The only other reason I can imagine it NOT doing that is the BIOS settings - all laptops have a setting to disable external bootup displays. 

Sorry we weren't more help, on the behalf of the entire Ubuntu community. :(

---

### Post by El Lance-O on 2009-03-02
I don't have a live cd close by right now, but that's basically what the IRC team told me to do as well.

Don't apologize, YOU and the others in this thread actually REPLIED, so you are fighting the evil just by doing that. :P

I'm just sick of being ignored all the time when I desperately need help, and this whole movement is based on community. It just seems like complete hypocracy to me.

I will keep trying and report back. Thanks again for the replies!

---

### Post by brian_p on 2009-03-02
> **El Lance-O said:**
> Look, I know how an external monitor works.

From your other thread you say you get a root prompt. Try repairing the machine from there. A file system check, perhaps.

---

### Post by El Lance-O on 2009-03-02
I know I didn't mention it in THIS post, but the whole problem is that my laptop won't boot because of an fsck error, none of which I can read because my external doesn't turn on until GDM or X is started.

Yes I get a root prompt, but I would like to see what I am doing before I just start inputting commands on a partially uncovered root prompt.

---

### Post by Truefire on 2009-03-02
Nice! You should be able to use basic directory commands to copy all data to an external drive. Can anybody share sone CLI wisdom here?

---

### Post by cariboo on 2009-03-02
You should be able to boot in recovery mode and copy your importat files from your home directory to your external drive. To mount your external drive at the prompt type:

```
 mount /dev/sdb1 /mnt
```

substitute your device label for the above example, then:

```
cd /home/<user_name>
```

where <user_name> is you user name, then:

```
cp -r * /mnt
```

this will copy all the files recursively to your mounted external drive.

If you need network access at the prompt:

```
dhclient eth0
```

substitute your network device for eth0 if different.

Just as a point everyone here answering questions is a volunteer. Don't expect a quick answer, as the person that could answer your questions may not have seen your question yet, and a little bit of politness goes a long way, instead of complaining about volunteers not answering your questions.

Jim

---

