---
title: "Getting rid of windows"
date: 2010-11-24
forum: New to Ubuntu
---

### Post by Dermot Doyle on 2010-11-24
Hi All,
I just did a clean install of 10.04 having used 8.04 for years on my laptop and I'm very impressed. Now I want to do the same on my other laptop dual booting 9.04 and Windows, but I want to get rid of windows altogether. Will the CD automatically replace both systems or will I have to tell it what to do? And if so, what do I tell it? Please bear in mind I'm barely computerate, though I have usually managed to follow advice on these forums with some extra prompting occasionally.
Cheers

---

### Post by arochester on 2010-11-24
Just tell it to use the whole disk.

---

### Post by Dermot Doyle on 2010-11-24
Thanks, I'll give it a go. I'll come back again if I get stuck.

---

### Post by Dermot Doyle on 2010-11-25
Right, I got stuck. I put in the disc I used before and it booted to it automatically. It ran exactly as it did before, UBUNTU and the dots below it going from red to white, then it went blank and nothing further happened. I tried it a couple of times, but still nothing. Does this suggest anything to anybody?
By the way it's a Sony Vaio if that's relevant.
Cheers

---

### Post by Rubi1200 on 2010-11-25
What graphics card do you have installed on the laptop in question?

---

### Post by heyho on 2010-11-25
I have had laptops that have been a bit picky about live cds, but the alternate install CD usually works.

3rd option down.

[http://releases.ubuntu.com/lucid/]("http://releases.ubuntu.com/lucid/")

---

### Post by Dermot Doyle on 2010-11-26
Hi Ruby, I have no idea, where should I look on 9.10 (not 9.04 as I previously said)?
Heyho, I didn't click on the link because I am using my newer laptop with 10.04 already on it. Is that a download I can put straight onto my other computer?
Thanks for the replies so far.

---

### Post by sandyd on 2010-11-26
> **Dermot Doyle said:**
> Right, I got stuck. I put in the disc I used before and it booted to it automatically. It ran exactly as it did before, UBUNTU and the dots below it going from red to white, then it went blank and nothing further happened. I tried it a couple of times, but still nothing. Does this suggest anything to anybody?
By the way it's a Sony Vaio if that's relevant.
Cheers

you need to use nomodeset.

Press esc/shift while computer is booting up.

press 'e' after the grub menu appears.

add 'nomodeset' (without quotes) to the end of the line that has "kernel" in it.

make sure theirs a space in between.

Press control+x to boot.

---

### Post by Dermot Doyle on 2010-11-27
Hi Sandyd,
I tried what you suggested, but when I pressed esc/shift I got something called 'Phoenix BIOS Setup Utility'. It had various headings, but nothing that would respond to pressing (selecting?)'e' and no line with kernel in it so I assume it wasn't the grub menu. Any other ideas of getting into the grub menu?
Cheers

---

### Post by Penguin=) on 2010-11-27
Ok, maybe you should get the ISO again and burn it to a disk.

Or you could try to aquire one from them via post, but that takes a long time rather than the 20 miniutes putting a ISO on a disk.

Try getting 10.10 to, it cmes with Wayyy.... more features than 8.04 and i think you will be more impresed with this.


If you don't want to do this, try leaving it on the screen it stays on for about 2 hours, it may come up with something new.

Anyway i hope this helps you.
Good luck.
Aaron

---

### Post by Dermot Doyle on 2010-11-27
Hi Sandyd,
I managed to get into the grub menu and did what you said, but the disc hasn't got any further than before. Any more ideas I could try? I'm downloading the alternate CD and I'll give that a go.

---

### Post by Dermot Doyle on 2010-11-27
Hi All,
I did what Heyho said and downloaded the alternative CD. It worked straight off and eventually told me I had succesfully loaded 10.04. However, when it restarted I got a blank screen with a cursor flashing in the top left corner and then the ubuntu image from the install disc flashed up for a second then everything went completely blank and nothing happened. I have checked that it is booting from the hard drive and tried it few times, but I get the same result every time. Any idea what to do now?
Cheers

---

### Post by Dermot Doyle on 2010-11-27
Hi All,
Just an update to say that I have followed some threads here and managed to get into the grub menu, pressed 'e' to edit and then added 'nomodeset' after 'splash' then cont-X to boot, but it hasn't worked. I can't find any other threads with exactly this problem. Can anyone help?
Cheers

---

