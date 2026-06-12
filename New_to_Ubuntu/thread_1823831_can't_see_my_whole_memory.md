---
title: "can't see my whole memory ?"
date: 2011-08-12
forum: New to Ubuntu
---

### Post by drsyntax on 2011-08-12
Hello,

I have **ubuntu 10.04** 64 bit edition, and I just added extra 2 GB RAM, which makes my total RAM 5 GB.

I can see that the total memory from BIOS is 5 GB, but using the free command on my ubutnu machine it returns that I have only 3.2 GB as per below :

```
             total       used       free     shared    buffers     cached
Mem:          3268        172       3096          0         31         74
```

However, when I checked the lshw command it returned the following:
```

*-memory:0
          description: System Memory
          physical id: 36
          slot: System board or motherboard
        *-bank:0
             description: DIMM DDR2 Synchronous 667 MHz (1.5 ns)
             vendor: JEDEC ID:00 00 00 00 00 00 00 00
             physical id: 0
             serial: 00000000
             slot: XMM1
             size: 2GiB
             width: 64 bits
             clock: 667MHz (1.5ns)
        *-bank:1
             description: DIMM DDR2 Synchronous 533 MHz (1.9 ns)
             product: M3 78T6553CZ3-CD5
             vendor: JEDEC ID:CE 00 00 00 00 00 00 00
             physical id: 1
             serial: 87A51CF8
             slot: XMM2
             size: 512MiB
             width: 64 bits
             clock: 533MHz (1.9ns)
        *-bank:2
             description: DIMM DDR2 Synchronous 667 MHz (1.5 ns)
             vendor: JEDEC ID:00 00 00 00 00 00 00 00
             physical id: 2
             serial: 00000000
             slot: XMM3
             size: 2GiB
             width: 64 bits
             clock: 667MHz (1.5ns)
        *-bank:3
             description: DIMM DDR2 Synchronous 533 MHz (1.9 ns)
             product: M3 78T6553CZ3-CD5
             vendor: JEDEC ID:CE 00 00 00 00 00 00 00
             physical id: 3
             serial: ED3342F1
             slot: XMM4
             size: 512MiB
             width: 64 bits
             clock: 533MHz (1.9ns)

```

What should I do to make ubuntu sees the whole 5 GB RAM ?

---

### Post by snip3r8 on 2011-08-12
Ubuntu 9.04 Jaunty Jackalope - If this is what you are running it may be the problem,I have seen that some older Distros only seem to pick up a max of 3gb of ram.Try A newer distro like natty.

---

### Post by drsyntax on 2011-08-12
I am using ubuntu 10.04

---

### Post by JRV on 2011-08-12
Duplicate post, sorry.

---

### Post by Hakunka-Matata on 2011-08-12
@drsyntax:  exactly what code did you use to produce the memory bank display of installed memory.  my system 10.10-32bit pae shows nothing similar with ```
lshw | grep memory
```

---

### Post by JRV on 2011-08-12
10.04 should see all the memory.

What does system monitor say?

Put the 2 gig sticks in banks 0 and 1, and remove the 512 meg sticks, and let us know what happens.

---

### Post by Hakunka-Matata on 2011-08-12
never mind, I got it.  Thanks

```
sudo lshw -class memory
```

---

### Post by drsyntax on 2011-08-12
> **JRV said:**
> 10.04 should see all the memory.

What does system monitor say?

Put the 2 gig sticks in banks 0 and 1, and remove the 512 meg sticks, and let us know what happens.

I removed the 512 MB sticks and nothing changed
here is what results when using free 
```
*-memory:0
       description: System Memory
       physical id: 36
       slot: System board or motherboard
     *-bank:0
          description: DIMM DDR2 Synchronous 667 MHz (1.5 ns)
          vendor: JEDEC ID:00 00 00 00 00 00 00 00
          physical id: 0
          serial: 00000000
          slot: XMM1
          size: 2GiB
          width: 64 bits
          clock: 667MHz (1.5ns)
     *-bank:1
          description: DIMM DDR2 Synchronous [empty]
          vendor: JEDEC ID:
          physical id: 1
          slot: XMM2
     *-bank:2
          description: DIMM DDR2 Synchronous [empty]
          vendor: JEDEC ID:
          physical id: 2
          slot: XMM3
     *-bank:3
          description: DIMM DDR2 Synchronous 667 MHz (1.5 ns)
          vendor: JEDEC ID:00 00 00 00 00 00 00 00
          physical id: 3
          serial: 00000000
          slot: XMM4
          size: 2GiB
          width: 64 bits
          clock: 667MHz (1.5ns)


```
here is the result of lshw 
```
*-memory:0
       description: System Memory
       physical id: 36
       slot: System board or motherboard
     *-bank:0
          description: DIMM DDR2 Synchronous 667 MHz (1.5 ns)
          vendor: JEDEC ID:00 00 00 00 00 00 00 00
          physical id: 0
          serial: 00000000
          slot: XMM1
          size: 2GiB
          width: 64 bits
          clock: 667MHz (1.5ns)
     *-bank:1
          description: DIMM DDR2 Synchronous [empty]
          vendor: JEDEC ID:
          physical id: 1
          slot: XMM2
     *-bank:2
          description: DIMM DDR2 Synchronous [empty]
          vendor: JEDEC ID:
          physical id: 2
          slot: XMM3
     *-bank:3
          description: DIMM DDR2 Synchronous 667 MHz (1.5 ns)
          vendor: JEDEC ID:00 00 00 00 00 00 00 00
          physical id: 3
          serial: 00000000
          slot: XMM4
          size: 2GiB
          width: 64 bits
          clock: 667MHz (1.5ns)

```

---

### Post by JRV on 2011-08-12
Run memtest from grub or from the CD and see what it says.

---

### Post by oldsoundguy on 2011-08-12
Install PAE

[http://linuxlookup.com/howto/use_more_4gb_memory_ubuntu_linux_32_bit](http://linuxlookup.com/howto/use_more_4gb_memory_ubuntu_linux_32_bit)

Sorry, just noticed 64 bit!!!

---

### Post by Hakunka-Matata on 2011-08-12
> **JRV said:**
> 10.04 should see all the memory.

What does system monitor say?

Put the 2 gig sticks in [COLOR=Red]banks 0 and 1[/COLOR], and remove the 512 meg sticks, and let us know what happens.

@JRV:  You suggested that to the OP.  The mem modules are in banks 0 and 3 though.  That might be important?

---

### Post by elgordodude on 2011-08-12
I think so. Something seems weird here in that he has 3268 megs of memory showing. It seems if the computer was only recognizing one 2 gig stick and the 2 512 sticks it would say 3072. So where did the other 196 megs come from?

A couple of guesses, but it's hard to say for sure.

1) The motherboard is looking for the sticks to be installed in pairs, if this is the case installing the 2 gigs in 0 and 1 and the 512s in 3 and 4 should solve the problem

2) The new 2 gig stick is defective, memtest will tell you for sure, and this seems likely except that the mobo recognises it and he hasn't reported any memory errors at startup. Also, the lshw output seems to recognise it fine, so how come something doesn't add up?

---

### Post by drsyntax on 2011-08-12
I performed a memtest and it also sees only 3268 M, and there was 89 Errors returned.

---

### Post by Johnb0y on 2011-08-12
are you using the 64bit version...?

*edit: scratch that... just noticed that it is... lol @ me! tried re-installing it? 

[http://www.ubuntu.com/download/ubuntu/download](http://www.ubuntu.com/download/ubuntu/download)

---

### Post by elgordodude on 2011-08-12
Given that you want 0, 89 is a lot. Definitely sounds like you got a bad chip. Here's an idea, what happens if you run the computer on only the new stick? Does the computer beep wildly at you now when it starts? POST should only beep once, more beeps likely indicates memory errors.

---

### Post by drsyntax on 2011-08-12
> **elgordodude said:**
> Given that you want 0, 89 is a lot. Definitely sounds like you got a bad chip. Here's an idea, what happens if you run the computer on only the new stick? Does the computer beep wildly at you now when it starts? POST should only beep once, more beeps likely indicates memory errors.

When I ran the system with only the new memory chip, it didn't beep at all.

Can the BIOS limit the memory delivered to the OS ?!

---

### Post by elgordodude on 2011-08-12
Did it run normally? Every bios I've heard of beeps once to acknowledge a successful POST. No beeps usually means a malfunctioning mobo speaker, or that audio has been manually disabled in bios, but if it doesn't beep at all then it could be trying to beep at you several times and we would have no way of knowing.

The motherboard can definitely limit the memory, especially when newer technologies are used on older technology. Here's a thought out of left field, any chance you're running a 756 meg gpu? If the mobo was factory limited to 4 gigs (because that was the theoretical maximum when it was built) then it could be counting that towards your 4 gig maximum, not common, but it's definitely happened, and it would cause roughly 3 1/4 gigs to show regardless of how much memory you put in. Even though your real memory "maximum" would be 8 gigs plus whatever you can get into the pcie slots, the board doesn't know how to deal with it.

So I'm definitely thinking that you got a bad chip and you should exchange it at the store. But, if you want to play with it a little more, you can try a few things.

1 Update the bios, can be a pain in the butt, especially on non windoze systems, but it's rarely a bad idea, and it might cause everything to fall into place.

2 Try another distro on a live cd. If it is a hardware problem then we should rule out ubuntu as the cause, so burn mint or opensuse, or any distro that you feel comfortable with and see if it still reports the 3.2 gigs of memory. Please, please always burn OSes at the lowest possible speed

3 Keep moving ram sticks around until it works right, not really recommended as I don't think it's a controller problem, and you can destroy some stuff if you're not experienced with doing it, but maybe....

---

