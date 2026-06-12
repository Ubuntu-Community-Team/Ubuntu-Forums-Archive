---
title: "archiving in Windows, extracting in Linux"
date: 2010-12-15
forum: New to Ubuntu
---

### Post by yc2 on 2010-12-15
Hello,

I must often manage my Linux server from Windows Internetcafes. I want to pack larger amounts of files into archives, upoload and extract the files.

I do not have direct access or SSH access to the server. Mostly I run php pages with bash commands like this:

shell_exec('tar xzf my_archive.tar.gz');

This works when I construct/compress the archive in a Linux environment, but I do not know how to do it in a Windows environment.

I have tried to use the program WinRar, set it to make a zip file and changed the extention to .tar.gz. However, it does not extract under Linux.

Please tell me how to make a compressed  archive under Windows that opens correctly under Linux.

I realize this is not a pure Ubuntu question, I still hope someone can help me, thanks.

---

### Post by sydbat on 2010-12-15
> **yc2 said:**
> Hello,

I must often manage my Linux server from Windows Internetcafes. I want to pack larger amounts of files into archives, upoload and extract the files.

I do not have direct access or SSH access to the server. Mostly I run php pages with bash commands like this:

shell_exec('tar xzf my_archive.tar.gz');

This works when I construct/compress the archive in a Linux environment, but I do not know how to do it in a Windows environment.

I have tried to use the program WinRar, set it to make a zip file and changed the extention to .tar.gz. However, it does not extract under Linux.

Please tell me how to make a compressed  archive under Windows that opens correctly under Linux.

I realize this is not a pure Ubuntu question, I still hope someone can help me, thanks.You can use the .zip extension without any problem.

---

### Post by yc2 on 2010-12-15
Thanks.

But what is wrong then ???

I often run commands like
shell_exec('tar xzf drupal-6.19.tar.gz');
and they work fine

However, if I make a zip archive myself, under Windows, using WinRar and try to expand it, the files will not extract, no matter which extension I use:
shell_exec('tar xzf test.zip');
shell_exec('tar xzf test.tar.gz');

My conclusion is that the archive is wrongly built somehow???

---

### Post by sydbat on 2010-12-15
> **yc2 said:**
> Thanks.

But what is wrong then ???

I often run commands like
shell_exec('tar xzf drupal-6.19.tar.gz');
and they work fine

However, if I make a zip archive myself, under Windows, using WinRar and try to expand it, the files will not extract, no matter which extension I use:
shell_exec('tar xzf test.zip');
shell_exec('tar xzf test.tar.gz');

My conclusion is that the archive is wrongly built somehow???Must be something corrupting. What, I am not sure.

---

### Post by CharlesA on 2010-12-15
> **yc2 said:**
> Thanks.

But what is wrong then ???

I often run commands like
shell_exec('tar xzf drupal-6.19.tar.gz');
and they work fine

However, if I make a zip archive myself, under Windows, using WinRar and try to expand it, the files will not extract, no matter which extension I use:
shell_exec('tar xzf test.zip');
shell_exec('tar xzf test.tar.gz');

My conclusion is that the archive is wrongly built somehow???

You'd have to use "**unzip**" to extract from zip files.

```
sudo apt-get install unzip
```

Also, [7-zip]("http://www.7-zip.org/") supports tar.gz format IIRC.

---

### Post by yc2 on 2010-12-15
> **CharlesA said:**
> You'd have to use "**unzip**" to extract from zip files.

```
sudo apt-get install unzip
```

Also, [7-zip]("http://www.7-zip.org/") supports tar.gz format IIRC.

Thank you. I do not have the privilege to install on the server right now. I am not sure what is installed.

tar is installed, though, of course.

**_Is it not possible to unzip using the z flag in tar?_**
shell_exec('tar xzf test.zip');

It works for f.ex. drupal.tar.gz archives from the drupal site  or for gallery-2.3.1-typical.tar.gz. Aren't these also zipped?

Thanks for taking your time.

---

### Post by CharlesA on 2010-12-15
You can run **unzip** and it'll say if it's installed or not.

You can't use tar for zip archives, so either use something like 7-zip to put them in a tar, or install unzip, if it's not already installed.

---

### Post by yc2 on 2010-12-16
Thanks a lot for valuable help.

This fortuntely works for archives zipped with WinRar:
$str = shell_exec('unzip test.zip | tar txf -');

(I am still not quite clear about the difference between zipping with WinRar and zipping with 7-zip but it is not of importance, I can now make archives under Windows and unzip them on the Linux server)

Thanks, thread solved.

---

### Post by CharlesA on 2010-12-16
Looks like you are unzipping an archive then piping it to tar to extract.

Is that what you want to do?

You can just use unzip to unzip zip files.

---

### Post by yc2 on 2010-12-16
I need to do this quite frequently and there is no other way I can do it, to my understanding.

I must run a Linux server from Windows remote computers sometimes.

I do not have SSH access to the server and neither do I have possibilities to install on the server. I mostly access the server in the described, indirect way (php shell_exec('bash command')). If I make larger copy commands they often time out since I access through php-http. I cannot send the files one by one through ftp since it takes too much time.

F.ex. updating drupal or gallery means replacing a lot of files on the server. I must therefore make my own drupal/gallery archive (with my unique filenames and modules), then upload it and often expand it "on top of" (replacing files if they exist) a folder with the same name on the server.

I really never need the tar. To me it is just an intermediate. I need to be able to make a compressed (quick to upload) archive under Windows, upload it and decompress/extract it (on top of a similarly named folder) on the server.

I think that answers your question?

Thanks for the help.

---

### Post by CharlesA on 2010-12-16
You can create tars on Windows using 7zip. That would probably be the easier option.

I was referring to this command:

```
unzip test.zip | tar txf -
```

You are unzipping the zip file and then piping the output to tar to extract (which wouldn't work, since it's already extracted.

---

### Post by yc2 on 2010-12-16
Thanks for pointing it out, I thought I first had to unzip with program unzip and then untar with program tar. This is obviously not necessary. (unzip does it all) The two commands below give the same (desired) result. I can obviously stay with the first one which is the correct. 

```
shell_exec('unzip test.zip');
shell_exec('unzip test.zip | tar txf -');

```

Right now I am happy since WinRar (option zip) is installed on my local desktop and unzip is installed on the remote server. if I get into problems I will remember your suggestion packing with 7-zip (on local) and unpacking w. tar -xzf (on server) as I interpret it.

Thanks for taking your time.

---

### Post by yc2 on 2010-12-16
My problem is solved.
Using the commands zip/unzip I can compress/extract archives that can be used/have been created under Windows (e.g. using WinRar).

However, I think I misunderstood you regarding 7-zip (Win). I have tried it a little and I do not think it can compress archives that can be extracted using "tar -xzf". One must still use unzip. (7-zip can create tar archives that are not compressed, though.)

When it comes to *function*, WinRar and 7-zip have the same abilities. They can compress/extract (under Windows) archives that can be extracted/have been compressed under Linux using unzip/zip.

I agree that your recommendation of 7-zip is right since I understand that 7-zip is free software. However, looking at the *function*, WinRar and 7-zip do the same thing.

There does not seem to be a way to create a ".tar.gz" archive under Windows. (meaning an archive that can be extracted by "tar -xzf")

To communicate with Windows using archives one MUST use zip/unzip.

At least this is how I have come to understand the situation.

---

### Post by CharlesA on 2010-12-16
You are correct in that 7-zip can only create non-compressed tarballs.

However, you can still extract them by using tar -xf

```
charles@lucid:~/Desktop$ ls Think*
ThinkGeek.tar
charles@lucid:~/Desktop$ tar -xf ThinkGeek.tar
charles@lucid:~/Desktop$ ls -ld Think*
drwxr-xr-x 2 charles charles    4096 2010-12-16 20:03 ThinkGeek
-rwxr--r-- 1 charles charles 4312064 2010-12-16 20:03 ThinkGeek.tar

```

---

