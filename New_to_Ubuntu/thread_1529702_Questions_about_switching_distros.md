---
title: "Questions about switching distros"
date: 2010-07-12
forum: New to Ubuntu
---

### Post by Troll_the_Great on 2010-07-12
Hello all!

I have a few questions about switching distros. My primary concern is if my settings will still be there after installing the new OS. I have a separate /home partition.
I had Ubuntu 10.04 and replaced it with Linux Mint Isadora (which is basically 98% Ubuntu) and all my settings were still there after the switch (even my wallpaper).
But if I switch to a distro witch is more different from Ubuntu (maybe an RPM based distro) than Mint, what then? Can I keep my settings?

---

### Post by bodhi.zazen on 2010-07-12
> **Troll_the_Great said:**
> Hello all!

I have a few questions about switching distros. My primary concern is if my settings will still be there after installing the new OS. I have a separate /home partition.
I had Ubuntu 10.04 and replaced it with Linux Mint Isadora (which is basically 98% Ubuntu) and all my settings were still there after the switch (even my wallpaper).
But if I switch to a distro witch is more different from Ubuntu (maybe an RPM based distro) than Mint, what then? Can I keep my settings?

With most distros, yes it will work.

The major problem you will have - users are identified by user id (uid) and not name.

```
id
```

Some distros, such as Ubuntu, the first user is uid = 1000 , other distros (Fedora) the first user is uid = 500. In the event of a uid mismatch you will have problems with permissions.

IMO best to make a separate /home , with a unique user name for each distro, you can copy or link your settings.

Personally, I keep a /data partition rather then a separate /home partition.

---

### Post by Troll_the_Great on 2010-07-12
So, the only problem would be user uid? All debian based distro have the same user uid? Do you know if Mandriva, or PC LinuxOS have the same user uid as Ubuntu?

---

### Post by bodhi.zazen on 2010-07-12
> **Troll_the_Great said:**
> So, the only problem would be user uid? All debian based distro have the same user uid? Do you know if Mandriva, or PC LinuxOS have the same user uid as Ubuntu?

Most rpm distros (Fedora for sure) start with  uid of 500. I think this includes Mandriva and PCLinuxOS as well.

One other thought , VirtualBox ? You can boot as many OS as you like in VBox.

After a while, with a few exceptions, most of these OS are mostly the same under the hood.

---

### Post by Troll_the_Great on 2010-07-12
> **bodhi.zazen said:**
> Most rpm distros (Fedora for sure) start with  uid of 500. I think this includes Mandriva and PCLinuxOS as well.

One other thought , VirtualBox ? You can boot as many OS as you like in VBox.

After a while, with a few exceptions, most of these OS are mostly the same under the hood.

What about the debian distros? Will there be a problem with user uid there?

---

### Post by bodhi.zazen on 2010-07-12
> **Troll_the_Great said:**
> What about the debian distros? Will there be a problem with user uid there?

Probably not.

---

### Post by ajgreeny on 2010-07-12
You could keep all your data files in a separate /data partition and then you can either have a smaller, but still separate /home partition for each distro, or you could even let the home folder be a part of root, as is the default if you let ubuntu install itself to a whole disk.  The size of a separate /home will be quite small if there is only the configuration files and folders in it, and no data files, (photos, docs, music, videos etc etc).

This may sound complicated, and I accept that it is a bit more so that trying to use a single /home partition, and sharing all your configs, but I would think that the sharing of everything in /home in that way will almost inevitably be a big problem.  Not all distros put the configs for things in the same named folders, so you could have problems there.

---

### Post by Paqman on 2010-07-12
> **Troll_the_Great said:**
> So, the only problem would be user uid?

The uid, and the settings themselves. You can get problems with the fact that different distros use different versions of the same apps, and have them set up slightly differently. It's possible that you could switch to a different distro, sort out the ownership issues, and have all your settings work perfectly, but it's just as likely that you'll get some weirdness, especially if you're switching to a distro that uses the same desktop environment.

In general, I agree with bodhi.zazen, it's best to use separate user accounts on separate distros, although sharing one /home partition is perfectly ok. You could have a go at sharing settings between them, but I think it could be quite fiddly to make work well, and wouldn't confer a huge advantage.

---

### Post by Troll_the_Great on 2010-07-12
> **Paqman said:**
> 
In general, I agree with bodhi.zazen, it's best to use separate user accounts on separate distros, although sharing one /home partition is perfectly ok. You could have a go at sharing settings between them, but I think it could be quite fiddly to make work well, and wouldn't confer a huge advantage.

Maybe I didn't make myself understood. I don't want to keep 2 distros, only one. I will format the boot partition and install the other OS and keep only /home.

---

### Post by marshmallow1304 on 2010-07-12
Debian starts at 1000, same as Ubuntu.

Like others have said, there may be some strangeness if the other distro uses different versions of programs.  Maybe you could start with a test install in a small partition (keeping your current distro) and mount the home partition read-only.

---

### Post by Troll_the_Great on 2010-07-12
Thank you all for your answers. I must go to sleep now, here is almost 1:00 AM, but I am still waiting for your opinions and comments and I will see them in the morning.
Good night all!

---

### Post by Paqman on 2010-07-13
> **Troll_the_Great said:**
> Maybe I didn't make myself understood. I don't want to keep 2 distros, only one. I will format the boot partition and install the other OS and keep only /home.

I still wouldn't attempt to recycle settings. Keep the data for sure, but create a fresh account in the new system.

---

### Post by HermanAB on 2010-07-13
Just make a new user account.

---

