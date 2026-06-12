---
title: "Help with shell scripting"
date: 2011-06-01
forum: New to Ubuntu
---

### Post by faint545 on 2011-06-01
Hey guys, I've currently came up with a quick script to do some mounting and syncing between two points of interest...

```
#!/bin/bash
# This synchronizes the TV directory of my homeserver with the local TV directory I have.
clear

# Mount folders first
sshfs alex@SomeDomain.net:/mnt/data/Users/Alex/Downloads/complete/ /mnt/source/
mount -t smbfs //wdtvlive.local/Media/ /mnt/dest/

# Begin synchronizing
rsync -urv --progress /mnt/source/TV/ /mnt/dest/TV/

# When done, unmount
umount /mnt/dest/
fusermount -u /mnt/source
```This script works just fine however I want to add additional features. I want the script to end if the mount has failed. How do I check if a mount point failed and how do I end the script premature?

---

### Post by seawolf167 on 2011-06-01
I'm by no means an expert bash-scripter, so there are probably easier ways of doing this, but to check if it is mounted, and mount it if it hasn't been mounted:

```

if
mount | grep /mnt/dest/ > /dev/null
then echo "/mnt/dest/ is mounted"
else echo "/mnt/dest/ is not mounted"
mount -t smbfs //wdtvlive.local/Media/ /mnt/dest/
fi

```

---

### Post by faint545 on 2011-06-01
@seawolf167, thanks. btw, out of curiosity...

this line ...

```
 mount | grep /mnt/dest/ > /dev/null
```

could you explain that? i know grep is used to find text in a file...

---

### Post by seawolf167 on 2011-06-01
mount displays the mounted items, pipes that to grep which searches for the string /mnt/dest/

If grep finds something (i.e. your mount point exists), it will output and highlight the appropriate searched for entry. Since this search entry has data in it (i.e. >0), it will be greater than /dev/null (which is the null device - think of it like an always empty black hole). So since anything found > always empty location, this will be TRUE, and execute the next part of the loop, else it switches to the else statement and tries to remount the device.

EDIT: a good bash scripting guide can be found [here]("http://mywiki.wooledge.org/BashGuide").

---

### Post by faint545 on 2011-06-02
I looked through the guide you posted and decided to do some exercises. This one particular one I am stuck on. It's seemingly simple and it's driving me nuts. I want to be able to compare two strings. One given as an argument and the other is hard coded.

```

USER="alex"
if ["$*" = "$USER"]
then echo "match!"
else echo "no match!"
fi
```but I keep getting this error

```

alex@Kerberos2:~$ ./test alex
./test: line 11: [alex: command not found
no match!

```

---

### Post by yeats on 2011-06-02
> If grep finds something (i.e. your mount point exists), it will output and highlight the appropriate searched for entry. Since this search entry has data in it (i.e. >0), it will be greater than /dev/null (which is the null device - think of it like an always empty black hole). So since anything found > always empty location, this will be TRUE, and execute the next part of the loop, else it switches to the else statement and tries to remount the device.

Sorry, but this is not correct... ;-).  The ">" in bash is not "greater than" but means "redirect the output".  In the case of 

```
 mount | grep /mnt/dest/ > /dev/null
```

it means "take the output of 'mount | grep /mnt/dest' and redirect it to /dev/null", which is (as correctly described) "like an always empty black hole".  Since you don't need to see the output in the messages in the console, you're "throwing it away."  

Hope that's helpful.

---

### Post by faint545 on 2011-06-02
> **yeats said:**
> Sorry, but this is not correct... ;-).  The ">" in bash is not "greater than" but means "redirect the output".  In the case of 

```
 mount | grep /mnt/dest/ > /dev/null
```it means "take the output of 'mount | grep /mnt/dest' and redirect it to /dev/null", which is (as correctly described) "like an always empty black hole".  Since you don't need to see the output in the messages in the console, you're "throwing it away."  

Hope that's helpful.

Ah.. thanks!

---

### Post by m_duck on 2011-06-02
> **faint545 said:**
> I looked through the guide you posted and decided to do some exercises. This one particular one I am stuck on. It's seemingly simple and it's driving me nuts. I want to be able to compare two strings. One given as an argument and the other is hard coded.

```

USER="alex"
if ["$*" = "$USER"]
then echo "match!"
else echo "no match!"
fi
```but I keep getting this error

```

alex@Kerberos2:~$ ./test alex
./test: line 11: [alex: command not found
no match!

```

That error comes about because ***[*** and ***]*** are actually commands, and thus need spaces between them and what follows/precedes them.

Also, ***=*** is an assignment operator - to compare two strings, use ***==***.

---

### Post by faint545 on 2011-06-02
> **m_duck said:**
> That error comes about because ***[*** and ***]*** are actually commands, and thus need spaces between them and what follows/precedes them.

omg, what a subtle syntax error. thanks so much.

---

### Post by seawolf167 on 2011-06-02
> **yeats said:**
> Sorry, but this is not correct... ;-).  The ">" in bash is not "greater than" but means "redirect the output".  In the case of 

```
 mount | grep /mnt/dest/ > /dev/null
```it means "take the output of 'mount | grep /mnt/dest' and redirect it to /dev/null", which is (as correctly described) "like an always empty black hole".  Since you don't need to see the output in the messages in the console, you're "throwing it away."  

Hope that's helpful.

Aye - I did post that incorrectly, thanks for catching it!

---

### Post by adam.webb on 2011-06-02
Have you tried the "double pipe" ||?

I am no expert at any of this, but my understanding is that anything after the || ```

```only gets used if the first command fails, ie ```
mount /dev/sdb5 || exit 0 
``` would mount /dev/sdb5 if it exists, and otherwise exit the script.

But as I said, I'm fairly new to the game, and this may either not be what you are looking for, or be completely wrong!

Adam

---

