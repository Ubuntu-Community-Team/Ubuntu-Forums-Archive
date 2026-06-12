---
title: "Permisions prob"
date: 2010-04-16
forum: New to Ubuntu
---

### Post by nnjond on 2010-04-16
Hi, 
I have the same username and password for two os's on separate HDDs but 
some of the files have little padlocks on them and -

.../DesktopB$ chmod 777 Witness\ to\ a\ snow\ miracle\ disc.ogg
chmod: changing permissions of `Witness to a snow miracle disc.ogg': Operation not permitted
nnjond@nnjond-desktop:/media/4254e869/home/nnjond/DesktopB$ 


Doesn't solve the prob.

Can you think of any solutions for rwx?

Thanks

---

### Post by bwhite82 on 2010-04-16
Check out the 'chown' command, read the man page first:

> man chown

---

### Post by doas777 on 2010-04-16
there probably isn't a good answer to your issue. the problem is uid's. the filesystem does not store permissions based on username, but on userid, so if your username is 'bob' on one box wit a uid = 1010 and the other one is named bob but has a uid of 1009, then bob 2 will never be recognized as the owner of bob 1's files.

using chown will just change which os currently owns it,so if you chown your files, and then reboot into the other os, you will have to chown them back, every time you switch os's.

what does 'ls -l' show for one of the folders you wish to access from both Os's?

---

### Post by nnjond on 2010-04-16
Thanks for your interest. Here is a segment of listed contents including the file (above) in question.

-rw-r--r--  1 root   root    758028288 2036-02-07 01:58 VTS_03_1.VOB
-rwxrwxrwx  1 nnjond nnjond      75740 2009-10-28 08:52 what-darwin-said-part-4-speciation.php.html
-rwxrwxrwx  1 nnjond nnjond      69744 2009-10-28 08:53 what-darwin-said-part-5-gradualism.php.html
-rwxrwxrwx  1 nnjond nnjond      70641 2009-10-28 08:53 what-darwin-said-part-6-gradualism-b.php.html
-rwxrwxrwx  1 nnjond nnjond      63668 2009-10-28 08:53 what-darwin-said-part-7-levels-of.php.html
-rwxrwxrwx  1    999    999    1845406 2009-04-20 16:50 What do we know.pdf
-rwxrwxrwx  1 nnjond nnjond       1728 2009-01-06 23:05 Why Map.vym
-rwxr-xrwx  1 root   root      2370542 2010-03-17 08:39 Wienberg_Prelude No 1_Op 100.ogg
drwxr-xr-x  6 nnjond nnjond       4096 2010-01-23 00:35 Wifi
-rwxrwxrwx  1 nnjond nnjond       3623 2009-10-28 15:14 win-friends.html
-rw-------  1 root   root      6236410 2010-02-05 12:53 Witness to a snow miracle disc.ogg
-rw-r--r--  1 root   root         1829 2010-01-18 07:57 Witness to a snow miricle disc.new
-rwxrwxrwx  1 root      999   25345304 2010-02-05 13:27 Witness to snow miracle.ogg

---

### Post by Calash on 2010-04-16
Did you try using sudo for the chmod command?

---

### Post by bwhite82 on 2010-04-16
> **nnjond said:**
> Thanks for your interest. Here is a segment of listed contents including the file (above) in question.

-rw-r--r--  1 root   root    758028288 2036-02-07 01:58 VTS_03_1.VOB
-rwxrwxrwx  1 nnjond nnjond      75740 2009-10-28 08:52 what-darwin-said-part-4-speciation.php.html
-rwxrwxrwx  1 nnjond nnjond      69744 2009-10-28 08:53 what-darwin-said-part-5-gradualism.php.html
-rwxrwxrwx  1 nnjond nnjond      70641 2009-10-28 08:53 what-darwin-said-part-6-gradualism-b.php.html
-rwxrwxrwx  1 nnjond nnjond      63668 2009-10-28 08:53 what-darwin-said-part-7-levels-of.php.html
-rwxrwxrwx  1    999    999    1845406 2009-04-20 16:50 What do we know.pdf
-rwxrwxrwx  1 nnjond nnjond       1728 2009-01-06 23:05 Why Map.vym
-rwxr-xrwx  1 root   root      2370542 2010-03-17 08:39 Wienberg_Prelude No 1_Op 100.ogg
drwxr-xr-x  6 nnjond nnjond       4096 2010-01-23 00:35 Wifi
-rwxrwxrwx  1 nnjond nnjond       3623 2009-10-28 15:14 win-friends.html
-rw-------  1 root   root      6236410 2010-02-05 12:53 Witness to a snow miracle disc.ogg
-rw-r--r--  1 root   root         1829 2010-01-18 07:57 Witness to a snow miricle disc.new
-rwxrwxrwx  1 root      999   25345304 2010-02-05 13:27 Witness to snow miracle.ogg

The file you mentioned previously is owned by 'root'. So you need to change it to your username:

> sudo chown **yourusername:yourusername** Wienberg_Prelude No 1_Op 100.ogg 

But, you will run into the problems that doas mentioned above.

---

### Post by doas777 on 2010-04-16
> **nnjond said:**
> Thanks for your interest. Here is a segment of listed contents including the file (above) in question.

-rw-r--r--  1 root   root    758028288 2036-02-07 01:58 VTS_03_1.VOB
-rwxrwxrwx  1 nnjond nnjond      75740 2009-10-28 08:52 what-darwin-said-part-4-speciation.php.html
-rwxrwxrwx  1 nnjond nnjond      69744 2009-10-28 08:53 what-darwin-said-part-5-gradualism.php.html
-rwxrwxrwx  1 nnjond nnjond      70641 2009-10-28 08:53 what-darwin-said-part-6-gradualism-b.php.html
-rwxrwxrwx  1 nnjond nnjond      63668 2009-10-28 08:53 what-darwin-said-part-7-levels-of.php.html
-rwxrwxrwx  1    999    999    1845406 2009-04-20 16:50 What do we know.pdf
-rwxrwxrwx  1 nnjond nnjond       1728 2009-01-06 23:05 Why Map.vym
-rwxr-xrwx  1 root   root      2370542 2010-03-17 08:39 Wienberg_Prelude No 1_Op 100.ogg
drwxr-xr-x  6 nnjond nnjond       4096 2010-01-23 00:35 Wifi
-rwxrwxrwx  1 nnjond nnjond       3623 2009-10-28 15:14 win-friends.html
-rw-------  1 root   root      6236410 2010-02-05 12:53 Witness to a snow miracle disc.ogg
-rw-r--r--  1 root   root         1829 2010-01-18 07:57 Witness to a snow miricle disc.new
-rwxrwxrwx  1 root      999   25345304 2010-02-05 13:27 Witness to snow miracle.ogg

the files that are owned by 999 are probably files owned by your user on the other OS, whereas the nnjond files are owned by your current user. if you were to login to the other os, you would probably see a mirror opposite effect.

---

### Post by nnjond on 2010-04-16
Success! Thanks. I can now play the file, but the padlock hasn't gone

---

