---
title: "foobar 2000 works great as audio converter"
date: 2010-03-22
forum: New to Ubuntu
---

### Post by paker on 2010-03-22
Foobar 2000 is the best audio converter that supports all audio formats that many ubuntu converters cannot, including wma format. Also, it is the best .cue splitter, losing no ID tags. No other ubuntu program can perserve ID info. Installation is a little complicated but all elements are here: [http://ubuntuforums.org/showthread.php?t=904145](http://ubuntuforums.org/showthread.php?t=904145).

foobar2000
Download (current version foobar2000_v1.1.7.exe) and install in wine. Select Full install.

ape
Download foo-input-monkey.zip. Unzip (extract) generates foo-input-monkey.dll. Move this to Home > Show hidden files > wine > Program Files > foobar2000 > components.

wma
download Window Media Lite (current version wmlite240.exe). install in wine (terminal > wine filename.exe). select 'Windows Media codecs' + 'Windows Media Format runtimes'. WM installs @ C: > Program Files > Windows Media Lite. No files to move here.

lame
Download lame zip file (current version lame3.98.4.zip) from rareware.org, codecs.com or any popular download sites. [DO NOT get ubuntu installation packages like tar gz.] Unzip. This generates lame.exe and lame_enc.dll. Copy lame.exe. Go to home > show hidden files > wine > program files > foobar2k. Paste. Copy .dll. Go to foobar2k > components. Paste.

flac
Download current flac (current version flac-1.2.1b.exe). Install in wine. Go to Home > Show hidden files > wine > program files > flac. Copy flac.exe. Paste to foobar2k.

PS: ubuntu 10.04LTS

---

