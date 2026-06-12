---
title: "Using sed for replacing an entry in fstab?"
date: 2011-07-16
forum: New to Ubuntu
---

### Post by mardose on 2011-07-16
Okay my good fellow Ubuntu'ers, here is my current dilemma. I'm in the process (a very long one, I might add) of writing a bash script to automate the softRAID  1, 0, and 10 setup on a pre-existing Ubuntu install and it would seem I've hit a small bump... After getting 100 lines into the script I realized that I am unsure of the proper syntax for supplementing an entry in /etc/fstab. 0_0 To stay short and to the point, here is what I'm trying to acomplish:

Replacing the /dev/sda1 entry with /dev/md0, /dev/sda2 with /dev/md1, and /dev/sda3 with /dev/md2

I'm sure the process is fairly simple, and I do remember that to (for instance) replace "John" with "Johnny it would look something like "sudo sed -e 's/John/Johnny/' > /some/random/document" but I guess my question is because of course the device entries start with a forward slash and for sed normally a forward slash would stand for "replace this with THIS" so what would be the correct way to accomplish this task? Thankyou very much in advance for your help, I'm sure it's something simple but I've been up for the last two days straight so that would be normal for me. :P Thanks again, and God bless.

---

### Post by Bachstelze on 2011-07-16
Actually you can use any character as a delimiter, not necessarily a forward slash:

```
firas@aoba ~ % cat foo.txt 
foo
bar
baz
firas@aoba ~ % sed s_ba_ga_ foo.txt 
foo
gar
gaz
firas@aoba ~ % sed sxbaxgax foo.txt
foo
gar
gaz
firas@aoba ~ % sed 's ba ga ' foo.txt
foo
gar
gaz

```

If you want to use a forward slash as a delimiter, put a backslash before any forward slashes in your expession to escape them:

```
firas@aoba ~ % cat test.txt 
/dev/foo
firas@aoba ~ % sed 's/\/dev\/foo/\/dev\/bar/' test.txt
/dev/bar

```

---

### Post by drs305 on 2011-07-16
Here's one way. Repeat for each. As was mentioned, you can use any delimiter. Rather than "/", I used "*" in the example.

```
sudo sed "s*/dev/sda1*/dev/md0*g" -i /etc/fstab
```****

---

### Post by mardose on 2011-07-16
This is amazing guys, thank you so much for your help. In the last hour I uncovered a dusty archive on sed usage, and just discovered that the easiest way for me was to write it as: [sudo sed 's|sda1|md0' /etc/fstab] etc... The other examples I was able to find online looked something like ////emfie\\\fe/\/\\/s\/\/e/\/\/e-e/\/\/\ lol and to be honest it felt slightly daunting. :P So again thanks much. Btw, the reason I decided to write a bash script for this is because even though I've messed around with Linux softRAID before, to  someone who isn't familiar with Linux (but would still like a RAID setup) it might make having a script do most of the work very helpful. (Actually, I currently have my Samba, Apache2, and PHP5 server running in a softRAID1 configuration) so anyhow, after I've finished and thoroughly tested it on my own rigs I'll probably post it up here for the general population. :) Third time and then I'll stop, thanks guys lol.

---

