---
title: "Experimental boot setup"
date: 2010-12-04
forum: New to Ubuntu
---

### Post by Blutkoete on 2010-12-04
Hello!

Is it possible to set up my computer like this:

- internal HD: Most of it /home (encrypted), some swap
- "/" and everything else on a bootable USB stick (I was thinking about 16 GB)

The idea was just for fun to use the USB stick as kind of a "key" for the computer - without it, you can't boot (or decrypt) the hard disk.

Is that possible or will I suffer some great speed/performance losses?

Thank you very much,

Blutkoete

---

### Post by QLee on 2010-12-04
Yes, you could do that, assuming your computer is capable of booting from USB. The "drive" will be limited to the USB speed your computer is capable of and the speed the flash drive is capable of, because there are fast ones and slow ones which correspond somewhat with the cost. Probably won't be as fast as your internal drive since you probably have a fairly recent and fast internal drive. Would you "suffer", depends on what you can tolerate for the purposes of this experiment you propose. Since it is an experiment, you should just try it.

---

### Post by sikander3786 on 2010-12-04
> without it, you can't boot (or decrypt) the hard disk.

That is not true I feel. The /home can still be decrypted and accessed from another Live CD/USB.

If experimental, just go for it!

But not a long term solution in my opinion. USB drives are much slower than most IDE, SATA disc and you'd definitely feel a lag in performance.

I would suggest to put your /home to the USB drive instead (if you are satisfied by the available space on your USB drive). That way, the OS would perform better.

---

### Post by Blutkoete on 2010-12-04
I'll try.

Yes, people will still be able to boot their USB stick and mount the hard disk, but well, isn't the encryption quite strong? I mean the password has like 32 letters or something (of course, a strong password won't protect a weak algorithm).

After testing it a little bit I'll see whether it is too slow or not and then might try something else.

Thank you!

---

### Post by QLee on 2010-12-04
[QUOTE=Blutkoete]...
Yes, people will still be able to boot their USB stick and mount the hard disk, but well, isn't the encryption quite strong? I mean the password has like 32 letters or something (of course, a strong password won't protect a weak algorithm).
...[/QUOTE]

Presumably, you can limit physical access to your machine.

They would need your passphrase.

Your government probably has security experts with the knowledge and systems with the computing power to get in. Likely the CIA of the US could also. It's highly unlikely your neighbour could do it. If you try to take it on a plane to another country and they ask you to turn it on, they may choose to seize it because it might appear odd to be carrying an encrypted drive. None of this matters, for your experiment.

---

### Post by Blutkoete on 2010-12-05
I tried it.

I put the /boot part on the USB stick and all the other stuff in a encrypted partition. While the booting process worked quite well (but slow), I wasn't able to test it anymore because I got an 'unknown fstype' error when trying to decrypt the hard disk. 

I don't know whether that was because the system got confused due to the boot setup or something else, but I switched back to a normal, simple system as I don't have time to investigate that further.

Maybe I'll try it all again later.

Thank you all!

---

