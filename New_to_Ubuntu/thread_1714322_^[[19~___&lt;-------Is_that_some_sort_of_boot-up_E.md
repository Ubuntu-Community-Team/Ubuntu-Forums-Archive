---
title: "^[[19~   &lt;-------Is that some sort of boot-up ERROR???"
date: 2011-03-25
forum: New to Ubuntu
---

### Post by suomalainen on 2011-03-25
Ubunteros,

When I bootup Ubuntu on my laptop, I always need to follow this process/steps:

1) Press F2 during bootup to enter BIOS
2) Scrool to boot order and choose USB External HDD as 1st bootable device
3) Ubuntu begins to boot up perfectly.

TODAY, after months of following the same process over and over something new is happening. Ubuntu appears to be booting up normally but then STOPS and the following code:

^[[19~

appears and then runs across the lcd for about 22 lines then stops for 10 seconds and continues on again and then the Ubuntu login screen appears....

This is real wierd. Has anyone seen this before? Is it a sign for whats about to come? Like a HDD crash or something? Any info would be most welcome.

Thank you!

---

### Post by Smart Viking on 2011-03-25
Hey it kinda looks like something is wrong with your keyboard, check if the <F8> key is stuck or something.

---

### Post by suomalainen on 2011-03-25
Smart Viking,


What leads you to believe it is the F8 key??? In any case It doesn't appear to be stuck.

Also, how come nothing bad happens when I boot up Win XP???? Shouldn't something happen it a key is stuck?

---

### Post by Smart Viking on 2011-03-25
This is why
```
laura@laura-desktop:~$ read
^[[19~

```
^ When I press F8

---

### Post by suomalainen on 2011-03-25
Smart Viking,

How are you actually running that code?

When I open terminal and press F8 I get a "~".

Your explanation will be appreciated....

Regardless, YOUR the MAN!!!!!

F8 was indeed stuck!!!!

My laptop is using a Yankee keyboard so that's why I didn't see the stuck key when I was looking. The key was stuck on my wireless keyboard! Can you imagine that a logitech product had stuck key? I got to write them about this.... 

Thank you very much for your support!!!

---

### Post by rbc on 2011-03-25
Open terminal, type the command “read” (without the quotes) and hit Enter. Now hit the F8 key. I must admit however, that after reading the man page for the read command, I have no idea what it’s actually used for, and using it, in the manner Smart Viking did, is never mentioned. Or maybe it is, and I’m just not smart enough to understand it

---

