---
title: "Killing the kernel"
date: 2010-05-22
forum: New to Ubuntu
---

### Post by Tahakki on 2010-05-22
I've got three kernels installed on my machine - two normal Linux kernels and a slightly older realtime kernel. My graphics card seems to work only on the realtime kernel. How can I remove the other two, or at least move the older realtime one to the top of my GRUB2 menu?

Ta! :)

---

### Post by emanuel.b on 2010-05-22
I usually use the Computer Janitor utility, under "System -> Administration -> Computer Janitor".

---

### Post by Tahakki on 2010-05-22
That application terrifies me. It always removes stuff I don't want it to - I stay well away. :P

---

### Post by emanuel.b on 2010-05-22
You can uncheck all the apps you don't want to get rid of...

---

### Post by 2hot6ft2 on 2010-05-22
This is the best I have seen on cleaning kernels by Admin-Amir. You may even learn some interesting things.
[Upgrade to NEW Kernel - Clean the old Kernels and packages]("http://forumubuntusoftware.info/viewtopic.php?f=66&t=4420")

But since this cleans old kernels and you want to remove the newest one I would either do it by command line or by searching for it by it's number in synaptic and selecting completely remove for the 3 kernel packages that have that kernel number.
:guitar:

---

### Post by Kafubie on 2010-05-22
Computer Janitor is something you use if you have alot of old kernals..  Just do it.  You will be fine and it won't screw up anything.

WORRY WART!

---

### Post by Tahakki on 2010-05-23
The only application that shows up in CJ is World of Goo, which, of course, I want to keep.

I'll try just manually removing them. Am I right in thinking it's these for each one?

linux-headers-[number]-generic
linux-headers-[number]
linux-image-[number]-generic

---

### Post by ShadowMage on 2010-05-23
> **Tahakki said:**
> I'll try just manually removing them. Am I right in thinking it's these for each one?

linux-headers-[number]-generic
linux-headers-[number]
linux-image-[number]-generic
I believe so. That's what I normally do anyway, when I want to remove a kernel; I find these 3 in synaptic by searching by number and I remove them from there. If you do remove them don't forget to update grub after by running
```
sudo update-grub
```

---

### Post by Tahakki on 2010-05-23
Removed one of them, but the other keeps trying to remove additionally some other packages, such as linux-image-generic. I assume I shouldn't let it do this?

---

### Post by ShadowMage on 2010-05-23
Tried this out again since I still had an old kernel. When I told synaptic to remove **linux-headers-[number]** it also wanted to remove **linux-headers-[number]-generic**, which is fine because we were going to remove that anyway. Then I had to find **linux-image-[number]-generic** to remove that as well. Clicked apply, 3 packages removed. Then sudo update-grub, everything's looking good.

Is it the same for you or is it trying to remove something else?

EDIT: Noticed you wrote "such as linux-image-generic". If it's trying to remove linux-image-[number]-generic, then don't worry that's fine, we want to remove this. But if it's trying to remove something other than these 3 (linux-headers-[number], linux-headers-[number]-generic, linux-image-[number]-generic), then I might be wary.

---

### Post by Tahakki on 2010-05-24
It's trying to remove all packages to do with generic kernels. My other kernel isn't generic; it's realtime.

---

### Post by Tahakki on 2010-05-25
I just removed what it wanted to remove - everything's working fine. :)

---

