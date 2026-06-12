---
title: "Authentication Failure!!!! -Help"
date: 2010-06-19
forum: New to Ubuntu
---

### Post by nabeelsadiq on 2010-06-19
So i just downloaded the ubuntu software from their website. I got it on the CD and i just wanted to try it on my computer. But when i started the computer with the CD in it, it asked me a username and password. But i never set a username or password. I tried pressing ctrl + alt + f1 and tried typing sudo adduser, but it wouldnt show up on the screen, it just shows a bunch of error messages. how do i solve this problem? Any help will be greatly appreciated.

---

### Post by Zeike on 2010-06-19
Can you please provide a link to the file you downloaded and the page you found it on?

Also, please post the errors you encountered.

Can you be more specific about what was on the screen when it asked you for a username/password?

---

### Post by byStanderone on 2010-06-19
well, that's really an abnormal behavior, when booting from a live ubuntu cd and it asks for a username-password. what particular version of ubuntu is that, and what is your present operating system? from what site did you download your ubuntu image from?

---

### Post by nabeelsadiq on 2010-06-19
i downloaded it from here :
[http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)

there was a box in the middle and it asked me for a username and then a password, after i entered them blank, it said Authentication Failure

Thanks

---

### Post by nabeelsadiq on 2010-06-19
i am running windows xp and the i got it from the ubuntu website: [http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)

---

### Post by Zeike on 2010-06-19
This is what I suggest you do:

Boot your computer with the cd in your drive.

You will see a picture of the ubuntu logo in the center of the screen.  There will be an image of a keyboard and little man at the bottom, when you see this, press any key to bring up the options menu.

Select your language, and then select "check cd for defects"

---

### Post by jtarin on 2010-06-19
> **nabeelsadiq said:**
> i downloaded it from here :
[http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)

there was a box in the middle and it asked me for a username and then a password, after i entered them blank, it said Authentication Failure

Thanks
Try these combinations. 
```
name:root password:root
name:admin password:admin
name:your name password:your password
```

I have seen this happen before with other distros, but I'm not familiar with it happening with his one. After you install I would change both or at least your password.

---

### Post by Elfy on 2010-06-19
Check the md5sum of the download as well.

[https://help.ubuntu.com/community/UbuntuHashes](https://help.ubuntu.com/community/UbuntuHashes)
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

In my experience here this is the result of either a bad burn or bad download.

---

### Post by nabeelsadiq on 2010-06-19
ok so this is really weird, so i hit ctrl alt f1 and the same error message is on there like 80 times! it says:

[5(the number is different each time] SQUASHFS error: Unable to read fragment cache entry [28c06a7]
[5(the number is different each time] SQUASHFS error: Unable to read page, block 28c06a7, size 8219

---

### Post by Zeike on 2010-06-19
> **nabeelsadiq said:**
> ok so this is really weird, so i hit ctrl alt f1 and the same error message is on there like 80 times! it says:

[5(the number is different each time] SQUASHFS error: Unable to read fragment cache entry [28c06a7]
[5(the number is different each time] SQUASHFS error: Unable to read page, block 28c06a7, size 8219

It sounds like you have errors on the disk.  Please do what I suggested above to verify this.

---

### Post by nabeelsadiq on 2010-06-19
but where do i type that code?
and to the errors mean anything to you guys?
would it be best for me to try to burn to a CD again, because this seams hopeless?
THanks

---

### Post by jtarin on 2010-06-19
> **nabeelsadiq said:**
> ok so this is really weird, so i hit ctrl alt f1 and the same error message is on there like 80 times! it says:

[5(the number is different each time] SQUASHFS error: Unable to read fragment cache entry [28c06a7]
[5(the number is different each time] SQUASHFS error: Unable to read page, block 28c06a7, size 8219

You can findsome validation for your errors [here]("https://help.ubuntu.com/community/SquashfsErrors")

---

### Post by nabeelsadiq on 2010-06-19
Zeike,
i do not have those options on my screen
i have the keyboard and the man and i can select a language but i do not see the "check cd for defects" option
thanks

---

### Post by Elfy on 2010-06-19
Please check the md5sum - I gave link above then reburn the cd at a slow speed.

---

### Post by nabeelsadiq on 2010-06-19
forestpiskie, i don't understand
i think i need to open a terminal for that and i don't know how to do that
sorry i'm very new to this stuff

---

### Post by nabeelsadiq on 2010-06-19
and how do i burn the cd slower?
thanks

---

### Post by lisati on 2010-06-19
> **nabeelsadiq said:**
> forestpiskie, i don't understand
i think i need to open a terminal for that and i don't know how to do that
sorry i'm very new to this stuff
For information about checking the md5sums, take a look here: [https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)
> **nabeelsadiq said:**
> and how do i burn the cd slower?
thanks

Have a look here: [https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

---

### Post by Elfy on 2010-06-19
> **nabeelsadiq said:**
> forestpiskie, i don't understand
i think i need to open a terminal for that and i don't know how to do that
sorry i'm very new to this stuff

[https://help.ubuntu.com/community/HowToMD5SUM#MD5SUM%20on%20Windows](https://help.ubuntu.com/community/HowToMD5SUM#MD5SUM%20on%20Windows)

show's how to use a free md5sum checker - no terminal.

No idea how to set the burn speed in what you are using - I don' know what you are using ;)

That assumes you are using windows to download and burn.

---

### Post by nabeelsadiq on 2010-06-19
so i ended up just burning it again at a slower speed and it worked
thanks for helping you guys, you're the best

---

