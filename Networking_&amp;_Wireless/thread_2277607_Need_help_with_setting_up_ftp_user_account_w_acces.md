---
title: "Need help with setting up ftp user account w access to multiple paths"
date: 2015-05-10
forum: Networking &amp; Wireless
---

### Post by kallen2 on 2015-05-10
I've finally got ftp login working with proftpd (vsftpd wouldn't let me use ftp without a key, and since i have friends who wont know how to make a keypair, i need to not use keys).

Problem, i cannot either give the ftp user account on my server access to multiple folders/paths nor change the home directory to an existing folder.

I cannot find any even half-usable links online that explains how to set up a user account that makes it easy for the person logging in to know what they have access to.  Since i don't want to give an ftp login root, and when i lock them in to their home dir default they have access to nothing, this is really not very helpful.

I am relatively new to linux, been learning a lot, but also seeing how non-intuitive the system is.  i'm definitely missing something, but there's no info online, only details on how to give write permission (which i only would give for an upload folder).  Is there a good resource online that explains how to set up an ftp user account and ensure that account has access to media folders (without stripping the ownership form my main admin account.   I was told i need to add a group, but seems only 1 group can be attached to a directory, which again makes things complicated for my primary administration access account (not logging in as root).

Any help that can get me started is appreciated.

---

### Post by kallen2 on 2015-05-11
anybody? Link to a good resource?

---

