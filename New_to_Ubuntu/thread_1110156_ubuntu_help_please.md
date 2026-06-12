---
title: "ubuntu help please"
date: 2009-03-29
forum: New to Ubuntu
---

### Post by zxy on 2009-03-29
I installed ubuntu with a partition and found out later i burned the ubuntu iso incorrectly...

I removed everything about ubuntu from add/remove programs but when i restarted my computer, the ubuntu option will still come up.

People tell me to run my restore cd and repair but all it does is bring back the ubuntu folder in windows vista also the ubuntu option is never gone.

I tried a fixmbr and that didnt work for me and when i run my repair cd and choose the command line option, its a x:\recovery tools\ but when i start vistan and go to run:fixmbr it says not found in c:\

Someone told me to run fixboot but I don't really know how to do it since i tried run: fixboot and it says not found and the X:\recovery tools\: (whatever I type, even help) brings up a error saying no such command.

---

### Post by yeats on 2009-03-29
What exactly are you trying to end up with ... Vista only?  If so, can you boot into Vista with GRUB (by selecting the Vista option at startup)?  If so, why not just use GRUB? - it does the job...

If you're trying to reinstall a dual-boot Ubuntu Vista, then post back about that too... your post isn't very clear about this :-).

---

### Post by llamabr on 2009-03-29
add/remove will only remove programs from within ubuntu.  Are you trying to remove ubuntu?

If so, you can either reinstall your other OS, or just write over the ubuntu partition, and use it with your other OS.  It should be able to format it for whatever filesystem you want.

---

### Post by jmszr on 2009-03-29
xyz,
     Did you install Ubuntu using Wubi?

---

### Post by zxy on 2009-03-29
I want it where when i on my computer only vista starts up, I dont like the grub thingy telling me to choose one....and if the third post is true? I can re install unbuntu correctly and it will fix my ubuntu error when i select it on the grub menu?

---

### Post by hyper_ch on 2009-03-29
It is advised to use a descriptive topic title, that means a topic title that gives some clue about the content in the thread itself...
 
 A generic topic title like "noob here" or "need help" does not help at all. As you may have noticed, just about everyone posting in here has some kind of a problem or issue or question ;)
 
 And it is also adviced to use seperate threads for unrelated problems so that you can mark each one individually as solved.
 
 Or in short terms: Help others to help you ;)
 
 See the forums policy, especially section II.2: [http://ubuntuforums.org/index.php?page=policy](http://ubuntuforums.org/index.php?page=policy)
 
 Also, when you are asked to post output from (config) files or from a command, use [noparse]```

```[/noparse] brackets around (each) output. That makes it also easier to read.

---

