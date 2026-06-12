---
title: "How to make a compressed archive smaller"
date: 2010-04-20
forum: New to Ubuntu
---

### Post by Crazedpsyc on 2010-04-20
I made a theme for gnome and now I want to publish it. the problem is, it must be no bigger than 1 megabyte, and it is 1.106... megabytes. I have already compressed it as a .tar.gz, and I don;t know what to do! help!](*,)

---

### Post by e4uforums on 2010-04-20
I would try 7zip.  There are a bunch of settings in there that will allow you to get different levels of compression based on what you are compressing.  I can't tell you what the best settings are to use, but it would be worth downloading it and playing around some.

---

### Post by jerome1232 on 2010-04-20
Compress it with the --best flag, or try bzip2 which has a better compression rate.

---

### Post by Drenriza on 2010-04-20
do ```
tar -cjtv (filename) (destination)
```
 
example
 
```
tar -cjtv wuubi.txt /home/cristian/Desktop
```
or something like that.

---

### Post by Crazedpsyc on 2010-04-20
drenriza, when I ran 
tar -cjtv (filename) (destination)
it said:
> 
tar: You may not specify more than one `-Acdtrux' option
Try `tar --help' or `tar --usage' for more information.

e4uforums, I tried p7zip, and it made a .7z archive and compressed it but it is still 1.1 mb
jerome1232, What command should I use with the --best flag? I tried bzip2 (if you mean as a .tar.bz2), but it was still about the same size, and still over 1 mb.

---

### Post by Drenriza on 2010-04-21
Okey, my mistake. Try
```
tar -cjfv (file/source) (destination)
```
example
```
tar -cjfv file.txt /home/cristian/Desktop
```
 
-c : Create
-j : bz2 extension
-f : Archive file
-v : Verbose

---

### Post by jerome1232 on 2010-04-21
Well I would try zipping it in a different stage, just tar up the files, then use the actual compression program to compress.

ie

```
tar cfv foo.tar /files/to/be/archived

bunzip2 --best foo.tar
```

at least I believe that's the usage of bzip, it's been awhile since i've used it and I have to dash off to work.


Good Luck, 7zip is probably your best bet, I believe it's one of the best compression algorithms.

---

### Post by Crazedpsyc on 2010-04-21
ok, sry if this is just because i'm a noob, but neither worked.
Drenriza, your option looked like it was going to work this time, but after the initial
> 
mike-laptop .themes # tar -c -j -f -v BloodMintGtk /home/mike/Desktop
tar: Removing leading `/' from member names
it just sat there for a long time.

jerome1232, your option also appeared to start working:
> 
mike-laptop .themes # tar cfv BloodMintGtk.tar /home/mike/.themes/BloodThemeGtk
tar: Removing leading `/' from member names
tar: /home/mike/.themes/BloodThemeGtk: Cannot stat: No such file or directory
tar: Exiting with failure status due to previous errors
no such file or directory? uhh, is that because it is hidden? or because I was running as root?
also, when I went to look at my .themes folder, look what I found!
BloodMintGtk  BloodMintGtk.tar  Clearlooks-2.0-blend  FireDragonGtk  -v
"-v" appears to be an empty archive (see attachment)

---

### Post by gmargo on 2010-04-21
> 
tar: /home/mike/.themes/BloodThemeGtk: Cannot stat: No such file or  directory

no such file or directory? uhh, is that because it is hidden? or because  I was running as root?
also, when I went to look at my .themes folder, look what I found!
BloodMintGtk  BloodMintGtk.tar  Clearlooks-2.0-blend  FireDragonGtk  -vNo, it's because you typed "Blood**Theme**Gtk", not "Blood**Mint**Gtk".

Try this:
```

cd $HOME/.themes
tar cf BloodMintGtk.tar BloodMintGtk
bzip2 BloodMintGtk.tar

```

---

### Post by Crazedpsyc on 2010-04-21
Oh lol thx for correcting that.
It's very tiny now! only 46 bytes! but tha's because it is empty :(
here's the output from the terminal:
> 
mike-laptop .themes # tar cf BloodMintGtk.tar BloodMintGtk
tar: BloodMintGtk: Cannot stat: No such file or directory
tar: Exiting with failure status due to previous errors
mike-laptop .themes # bzip2 BloodMintGtk.tar
bzip2: Output file BloodMintGtk.tar.bz2 already exists.
mike-laptop .themes # 
the "already exists" part is because this is this second time I ran it, the first time it didnt say anything there. it put the BloodMintGtk.tar.bz2 in something like /proc/xxxx/cwd/, which is a shortcut. I went there and copied it to /root/, opened it, and it was empty.

UPDATE:I just tried compressing it as a .tar.7z, and it is smaller that the others, but still too big a bit too big. the other compression algorithims I have are .tar.bz2 .tar.gz .tar.lzma .tar .zip .rar .jar .exe .cbz .cbr and .ar

UPDATE 2:here are the sizes of my theme compressed with each of those:
zip 1175058 bytes
tar.lzma 1164285
tar.gz 1160455
tar.bz2 1167336
tar.7z 1164648
tar 1239040
rar 1175394
jar 1178280
exe 1522742
cbz 1164102
cbr 1175394
ar 1184166
7z 1164102

and next will come the sizes of the ones that can be compressed again with different algorithms

Ok, nevermind, the nly one that can easily usefully be recompressed is the .ar, and it doesn't get much smaller with 7z of bz2

---

### Post by _0R10N on 2010-04-21
Yeah! 7zip is the best choice I know when file compression is crucial!... you have to download it from the repositories.

Kind regards!

_0R10N >>

---

### Post by gmargo on 2010-04-21
> mike-laptop .themes # tar cf BloodMintGtk.tar BloodMintGtk
tar: BloodMintGtk: Cannot stat: No such file or directory

What directory are you in?  Tar says you're in the wrong place or you've misspelled the directory name.

And what in the world are you doing it as root for?  Never use root for mundane tasks; only for system administration.

---

### Post by jerome1232 on 2010-04-22
Just a side thought, you say your making a theme right? Does it have alot of already compressed files in it? Such as jpeg's?


If so those images will not compress much, possible even bloat a bit. I would consider reducing the image quality slightly to compensate if this is the case.

---

### Post by durand on 2010-04-22
Maybe upload it to an upload website like mediafire or something similar? On compression, I'd suggest using the windows version of 7zip in wine. It has a very good set of compression features. The linux version seems to be commandline only, with basic integration in the default file extractor.

---

### Post by Crazedpsyc on 2010-04-23
Oh thx! I missed those last 4 replies becuae they werent visible to me until I used hybrid view mode!
I use a terminal that is not root, but close (modified admin user) with gksudo -u onetwothree so I don't have to put in my 47 character password every time I use sudo lol! Don't worry, my superadmin can do everything root can except access the network, and my security tools. thanks for the tip on Mediashare! I was looking for something like that, but couldnt find a good free one. no I don't have any compressed files in my theme at all. I was in .themes! right where BloodMint.tar was!

---

### Post by Crazedpsyc on 2010-04-23
I didnt think that last reply worked lol! here's the <a href="http://www.mediafire.com/file/4zfztujgnig/BloodMintGtk.tar.bz2">theme!</a>

---

