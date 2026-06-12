---
title: "WARNING &quot;encrypt home folder&quot; basically cuts your hard drive space in half."
date: 2011-07-30
forum: New to Ubuntu
---

### Post by Isaacgallegos on 2011-07-30
I'm just learning about this, but I figure I'd start warning people because it wasn't clear to me. I'm a general computer user, not some computer science expert. I'm sure many other new users might not be experts in computer science. 

**When you first install ubuntu you have an option to "encrypt home folder". _Checking this will cause your home folder to grow at twice the normal rate. _ Again, this is common knowledge to some users, but not new general users, which ubuntu is meant for. **

I'm still trying to figure out how to undo the mistake with out reformatting the whole drive, but that's unlikely. I think reformatting might be the only real solution. 

I've asked for help and the response was:

"LOL 

This is normal behavior for Ecryptfs."



Then I got a link to the manual regarding installing and general use of this encryption system. This was from a high level user and he didn't even know how to deal with removing the encrypted/backup folder.  I'm guessing removing it is not a really well known thing. 

**(edit: that high level user commented again with more info. Basically there is no solution other than reformatting your computer)**

Again this is just an FYI to my fellow Ubuntu users. Stay safe! Take care!

---

### Post by scruffyeagle on 2011-08-12
> **Isaacgallegos said:**
> I'm just learning about this, but I figure I'd start warning people because it wasn't clear to me. I'm a general computer user, not some computer science expert. I'm sure many other new users might not be experts in computer science. 

**When you first install ubuntu you have an option to "encrypt home folder". _Checking this will cause your home folder to grow at twice the normal rate. _ Again, this is common knowledge to some users, but not new general users, which ubuntu is meant for. **
<snipped>


Thanks for posting this. I had no idea... I've got a solution, which I'll be putting into use later tonight on a couple of encrypted home folders. You see, there IS a way to deal with an encrypted home folder, other than wiping out your entire installation. If I understand the option I said "yes" to correctly, what's being encrypted is strictly the user profile's home directory. I think that doing the following will be a minimum-damage solution:

1) Login as admin. Create a new user with the same security profile as the one which was encrypted. This time, not selecting encryption.
2) Logout & log back in as the encrypted user. If you have a flash drive, copy all the information you want to save onto the flash drive. The goal here is to get it out of the system temporarily for safekeeping. Floppies or Ubuntu One would work, too.
3) Logout & log back in as admin. Wipe out the encrypted user profile, selecting the option to delete all files.
4) Logout & log back in as the new unencrypted user profile. Copy the data you'd set aside into the new user profile's home directory.

Tah-dah! Done.

---

### Post by mcduck on 2011-08-13
Actually I'm absolutely sure you've misundrestood the situation, and the developer's answer as well. :)

Since directories encrypted with encryptfs are mounted as *virtual filesystems*, many disk space monitoring tools will show the space of both the actual, encrypted files, and the mounted virtual filesystem. However only the encrypted files actually exist on your hard drive and take space there.

The developer more than likely just tried to tell you that it's normal that the used disc space is *reported* twice. Not that it would actually *use* twice the disc space. :)

Instead of using any graphical tool, like the Disk Usage Analyzer (which definitely has a bug with virtual file systems), try running "df -h" in a terminal to check your used & available disc space.

---

### Post by 3rdalbum on 2011-08-13
> **mcduck said:**
> Actually I'm absolutely sure you've misundrestood the situation, and the developer's answer as well. :)

Since directories encrypted with encryptfs are mounted as *virtual filesystems*, many disk space monitoring tools will show the space of both the actual, encrypted files, and the mounted virtual filesystem. However only the encrypted files actually exist on your hard drive and take space there.

I'd agree with this assessment; there are a lot of threads where people get confused about reported disk space because they've got other disks and other partitions mounted. These add to the reported capacity and reported use; however, people tend not to notice the higher reported capacity. Everything in the filesystem is being counted - mounted disks included, because they are mounted inside the filesystem.

---

### Post by mastablasta on 2011-08-13
encrypted files might have a bit larger capacity (due to the encryption) but this doesn't mean they are twice as big. so as mentioned, it's just the way they are reported to the system.

---

### Post by scruffyeagle on 2011-08-14
> **mcduck said:**
> Actually I'm absolutely sure you've misundrestood the situation, and the developer's answer as well. :)

Since directories encrypted with encryptfs are mounted as *virtual filesystems*, many disk space monitoring tools will show the space of both the actual, encrypted files, and the mounted virtual filesystem. However only the encrypted files actually exist on your hard drive and take space there.

The developer more than likely just tried to tell you that it's normal that the used disc space is *reported* twice. Not that it would actually *use* twice the disc space. :)

Instead of using any graphical tool, like the Disk Usage Analyzer (which definitely has a bug with virtual file systems), try running "df -h" in a terminal to check your used & available disc space.

Ahhh... I see. Thanks for clarifying this. Luckily, I didn't get around to applying my "solution" on any encryted profiles last night. Now, I can see that it's not necessary. So, you're saying that
```
df -h
```
will ignore the virtual file system?

---

