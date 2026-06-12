---
title: "Install 11.04 won't complete"
date: 2011-05-02
forum: New to Ubuntu
---

### Post by mike-in-nc on 2011-05-02
I am totally new to Ubuntu, though I've used computers since 1967. I have used many different operating systems, but currently, I am most familiar with Windows.

I am trying to install Ubuntu 11.04 from a CD that I burned from a downloaded image. The target computer has a 6-yr old ASUS motherboard, 4Gb of RAM, and a 1Tb WD Caviar Green drive. The video card works fine, at least during the install.

The install runs (and runs at native resolution of the attached LCD), but the installation never finishes. It goes past the point where I enter username and password and then it displays several screens with information about Ubuntu (Thank You; Welcome To...; Find even more software, etc.). The installation then seems to stall. The disk-activity light is on continuously, but the progress bar doesn't move. I can't find any way to get more status information than that.

Any clues?

---

### Post by mike-in-nc on 2011-05-02
Now I am looking at 'kern.log' and there is a long, and growing, list of messages about "Unhandled sense code", "BMDMA stat 0x4", and "failed command: READ DMA EXT".  The install seems to be in a loop, trying over and over again to do something with the CD drive.

---

### Post by Rex Bouwense on 2011-05-02
Since you have been using computers since 1967, I sort of hesitate to make some comments but here goes.  Ignore anything that you already did.  
Did you md5sum the downloaded ISO?  Did you burn the image to the CD at the lowest speed possible?  How long did you wait while the progress bar was stalled before you gave up?  Sometimes it appears that it isn't doing anything while installing.  Most versions of Ubuntu do however install within 30-40 minutes.  When you were making entries did you tick also install updates while installing?  That would increase the install time by a little.

---

### Post by KL_72_TR on 2011-05-02
I would recommend to download a new image and make a new CD.
Two weeks ago I downloaded 11.04 and the image file was .... 3.9 GB !!!
After the installation including the online updates ~30min. Ubuntu was very slow and a lot of bugs.
I had to download it again and that resolved the problem.

---

### Post by mike-in-nc on 2011-05-02
> **Rex Bouwense said:**
> Since you have been using computers since 1967, I sort of hesitate to make some comments but here goes.  Ignore anything that you already did.  
Did you md5sum the downloaded ISO?  Did you burn the image to the CD at the lowest speed possible?  How long did you wait while the progress bar was stalled before you gave up?  Sometimes it appears that it isn't doing anything while installing.  Most versions of Ubuntu do however install within 30-40 minutes.  When you were making entries did you tick also install updates while installing?  That would increase the install time by a little.

Hi Rex. Thanks for your reply, and please don't hesitate. Things have changed since 1967! --and I'm a novice at Ubuntu.

I just tried installing from the *other* optical drive in the computer. That drive, being a few years newer, may support a larger command set. The install seemed to go successfully, though (1)it reported some files couldn't be deleted successfully, and (2) I wouldn't shut down.  Well, maybe progress, maybe not.  

P.S. I did check the md5 on the ISO.

---

### Post by mike-in-nc on 2011-05-02
Oh, no, I am wrong . . . I didn't check the md5. I was thinking of another installation. In fact, I can't even *find* what the md5sum should be for the iso.

I did find some help on the Ubuntu web site about turning off DMA on the optical drives. This seems pertinent. However, the tips show how to do that from a console!  The computer has no OS, so no console, and I can't find a way to get the installer to run a console for me to use. This seems perverse, but probably I am just missing something.

P.S. The computer won't boot from the previous install.

---

### Post by sandyd on 2011-05-02
[https://help.ubuntu.com/community/HowToMD5SUM#MD5SUM%20on%20Windows](https://help.ubuntu.com/community/HowToMD5SUM#MD5SUM%20on%20Windows)

---

### Post by mike-in-nc on 2011-05-02
When I installed from a pen drive, the installation ran fine, with none of the errors noted above. But when I restarted, Ubuntu wouldn't run.

I was just trying out Ubuntu before I donated this old computer to Free Geek. I'm stopping here.

Thanks, everyone, for the help. Case closed.

Mike

---

### Post by mike-in-nc on 2011-05-02
One final note -- it seems the hard disk in the computer was flaky. I was able to install successfully from a pen drive to a different hard disk. Once installed, it is an impressive OS.

---

### Post by mike-in-nc on 2011-05-03
> **sandyd said:**
> [https://help.ubuntu.com/community/HowToMD5SUM#MD5SUM%20on%20Windows](https://help.ubuntu.com/community/HowToMD5SUM#MD5SUM%20on%20Windows)

Thanks, Sandy. I guess it would be too straightforward for Ubuntu to put the hash on the same page as the download. Anyway, next time I need it, I know where to look -- thanks again.

---

### Post by Solstice Bahai on 2011-05-03
Here's hoping you don't give up on Ubuntu!! unlike yourself, I am not all that clued up on computers, but I am a complete novice regarding linux, of ANY distro, and like most are used to Windows (in that I don't concern myself too much with its inner workings, as long as "it does what it says on the tin"). I am 49, unemployed and willing to learn something new, so I have gone with Ubuntu on this netbook!!:D
All the best to you Sir!:)

---

### Post by mike-in-nc on 2011-05-03
Thank you -- I have not given up but need Windows for my work.  M.

---

### Post by Solstice Bahai on 2011-05-03
Windows for work, Lol, well  a lot of people do, guess it will be a fair while before Linux will be as ubiquitous as windows in the work place:D In any case my hat is off to you, all the best Sir!:popcorn:

---

### Post by pacman5 on 2011-05-03
> **mike-in-nc said:**
> The install runs (and runs at native resolution of the attached LCD), but the installation never finishes. It goes past the point where I enter username and password and then it displays several screens with information about Ubuntu (Thank You; Welcome To...; Find even more software, etc.). The installation then seems to stall. The disk-activity light is on continuously, but the progress bar doesn't move. I can't find any way to get more status information than that. Any clues?

Same thing happens for me. Downloaded the ISO, mdsum-checked it, ran it, the "Choose Keyboard" bit doesn't work, disk is running for hours but bar doesn't move.

I had previously tried a different route - upgrading from my Ubuntu 10.01 - but that just ended with a fuzzy pointer, fuzzy menu bar icons, and then a total freeze-up.

So I've now gone back to the good old reliable Ubuntu 10.01 LTE and see from various postings that I'm not the only one with 11.04 installation problems. As a Linux/Ubuntu admirer who lives in hope that Linux desktops might one day become mainstream I am disappointed and wonder why there has been all this premature Ubuntu 11.04 hoopla. I could probably get Ubuntu 11.04 to work by beavering away for hours punching in terminal commands and downloading modules with arcane names but Ubuntu really should be beyond that stage in 2011. It looks as if I, and possibly others, should wait a few months until Ubuntu 11.04 has had the wrinkles sorted out before trying to install it.

---

