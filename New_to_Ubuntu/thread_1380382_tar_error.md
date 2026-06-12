---
title: "tar error"
date: 2010-01-13
forum: New to Ubuntu
---

### Post by stewie17 on 2010-01-13
Hi all!

I've checked the forums to see if someone else had this issue. However, it doesn't seem that anyone has, so here is my problem. I'm trying to install Passenger for Ruby. Now, I have downloaded the tarball from RubyForge, but when I attemt to extract I get this error:

```

# tar xzvf ~/passenger-2.2.4.tar.gz
tar: /root/passenger-2.2.4.tar.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors

```

Does anyone have any ideas as to what I did wrong and how to fix the problem? Thanks in advance for any help.

---

### Post by Sef on 2010-01-13
> Does anyone have any ideas as to what I did wrong and how to fix the problem? Thanks in advance for any help.

Where did you download the package to?  Are you there?

---

### Post by mitch_feaster on 2010-01-13
Are you sure the file actually exists at that location? Post the output of ls /root. You might have downloaded the tar to your user home directory, logged in as root, and then tried to reference the file with ~ (which will expand to /root when logged in as root)...

---

### Post by arochester on 2010-01-13
Look at "How to install ANYTHING in Ubuntu!" on [http://amitech.50webs.com/installing/index.php.html](http://amitech.50webs.com/installing/index.php.html)

After you have extracted the file you need to navigate, move, into the directory you have extracted.

---

### Post by stewie17 on 2010-01-13
Following the instructions at [http://library.linode.com/web-frameworks/ruby-on-rails/ruby-on-rails-nginx-ubuntu-9.04](http://library.linode.com/web-frameworks/ruby-on-rails/ruby-on-rails-nginx-ubuntu-9.04), I have the file in root.

This is what I've done so far:
```

cd /root
wget http://rubyforge.org/frs/download.php/59007/passenger-2.2.4.tar.gz
cd /opt
tar xzvf ~/passenger-2.2.4.tar.gz


```

---

### Post by arochester on 2010-01-13
I wait to be corrected but that does not make sense to me.

You move to the /root folder and download there.You don't decompress there.

You then move to the /opt folder and try to decompress from there. BUT ~/passenger-2.2.4.tar.gz ...is the Home file??? 

"~" means the Home file...

---

### Post by stewie17 on 2010-01-13
> **arochester said:**
> I wait to be corrected but that does not make sense to me.

You move to the /root folder and download there.You don't decompress there.

You then move to the /opt folder and try to decompress from there. BUT ~/passenger-2.2.4.tar.gz ...is the Home file??? 

"~" means the Home file...

That's the instructions. I get the same error anyway I try to decompress the file. I did 
```
mkdir passenger-2.2.4
```
in /opt, then ran
```

tar xzvf passenger-2.2.4.tar.gz opt/passenger-2.2.4/

```

The result:
```

tar: opt/passenger-2.2.4: Not found in archive
tar: Error exit delayed from previous errors

```

---

### Post by stewie17 on 2010-01-13
> **arochester said:**
> I wait to be corrected but that does not make sense to me.

You move to the /root folder and download there.You don't decompress there.

You then move to the /opt folder and try to decompress from there. BUT ~/passenger-2.2.4.tar.gz ...is the Home file??? 

"~" means the Home file...
Thanks. I understand what went wrong here. I moved the file into /opt and then extracted. However, I wasn't able to use Apache, but no matter -- I was able to set up Nginx.

---

