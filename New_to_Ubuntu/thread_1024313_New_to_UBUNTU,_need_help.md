---
title: "New to UBUNTU, need help"
date: 2008-12-28
forum: New to Ubuntu
---

### Post by ronhall42 on 2008-12-28
I loaded unbuntu 8.1 under windows xp and when booting ubuntu, I was required to enter a user  id and a pass word.  I do not remember setting up a userid but did set up a pw which I know.  Don't know userid so how can I boot and  fix the id??  Would appreciate an email to [email]ronhall621942@aol.com[/email] if you will.  I'll of course check the ubuntu forum as well. Thanks.

---

### Post by sayems on 2008-12-28
If you forgot you password for your ubuntu system you can recover using the following steps

Turn your computer on.

Press ESC at the grub prompt.

Press e for edit.

Highlight the line that begins kernel ………, press e

Go to the very end of the line, add rw init=/bin/bash

press enter, then press b to boot your system.

Your system will boot up to a passwordless root shell.

Type in passwd username

Set your password.

Type in reboot

---

### Post by chrisod on 2008-12-28
It sounds like the OP installed with Wubi - I don't think there will be a grub prompt. Have you tried your windows login? I've never used Wubi but since it is a Windows program it may have just used your Windows userID.

---

### Post by snova on 2008-12-28
> **sayems said:**
> Press ESC at the grub prompt.

Press e for edit.

Highlight the line that begins kernel &#8230;&#8230;&#8230;, press e

Go to the very end of the line, add rw init=/bin/bash

Alternatively, you could just select the line ending in '(recovery mode)'. ;)

But this only fixes the password, and that isn't the problem... it's the username.

So try this. Boot into recovery mode and type 'ls /home'. The output should include the username.

> Would appreciate an email to [email]ronhall621942@aol.com[/email] if you will. I'll of course check the ubuntu forum as well.

Please don't ask for private support...

---

### Post by sayems on 2008-12-28
chrisod your absolutely right it is he is windows login username. Ronhall42, I think you should try login with your Windows username.

---

### Post by fooman on 2008-12-28
when you get to the ubuntu login screen...the username should be visible in the bottom right corner of the screen, followed by //

type that name into the username box and press enter followed by your password.

hope that helps.

---

### Post by snova on 2008-12-28
> **chrisod said:**
> It sounds like the OP installed with Wubi - I don't think there will be a grub prompt. Have you tried your windows login? I've never used Wubi but since it is a Windows program it may have just used your Windows userID.

> **sayems said:**
> chrisod your absolutely right it is he is windows id

In this case, log in with your Windows username (which I believe will be your full name). And I'll remember that for the future...

---

### Post by hyper_ch on 2008-12-29
It is advised to use a descriptive topic title, that means a topic title that gives some clue about the content in the thread itself...

A generic topic title like "noob here" or "need help" does not help at all. As you may have noticed, just about everyone posting in here has some kind of a problem or issue or question ;)

And it is also adviced to use seperate threads for unrelated problems so that you can mark each one individually as solved.

Or in short terms: Help others to help you ;)

Also, when you are asked to post output from (config) files or from a command, use [noparse]```

```[/noparse] brackets around (each) output. That makes it also easier to read.

---

