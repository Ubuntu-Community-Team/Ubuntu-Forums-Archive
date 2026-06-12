---
title: "Permissions and access problem"
date: 2011-02-09
forum: New to Ubuntu
---

### Post by constellanation on 2011-02-09
Background: I finally got around to copying over the data from a 6yr old mac hard drive last night.  After much googling, I was able to copy it from the old drive to my current ubuntu machine, using two nautilus windows.

Currently the contents of the drive are sitting in my root folder, where I can view them (and do other small things like delete them)
However I still have no permissions to do anything else with them.

I've tried a number of chmod combinations, ritual dances, etc... but I can not do what I want with these files, which is move them from my root folder to say my desktop and have the normal permissions of most files. Advice? suggestions?

---

### Post by robsoles on 2011-02-09
if the files are at /myoldmacfiles/* then```
sudo mv /myoldmacfiles ~/Desktop/
```will move them to your desktop, following on using my example of 'myoldmacfiles' as the folder name that contains them```
cd ~/Desktop/myoldmacfiles
sudo chown -R [COLOR="Blue"]my-user-name:my-primary-group[/COLOR] *
chmod -R 700 *
```NOTE: change the stuff in blue to match YOU.

Now the files belong to you and only you have access (aside from root unless your home directory is encrypted).

To find out if I am right and the files belong to root (or somebody aside from you at least) then enter```
ls -al
``` before the 'chown' command in previous code block and look at the owner of those files.

Any good?

---

### Post by constellanation on 2011-02-09
I think I need something to imply that it's a directory, the sudo mv command gives me 'cannot move directory is not empty'

---

### Post by jroa on 2011-02-09
Have you tried using the asterisk with the directory name?

```
mv *originaldirectory* newdirectory*
```

---

### Post by constellanation on 2011-02-09
I think my problems are solved, once I got past my mistakes, Thanks!!

ok got the files to move, two mistakes first was i needed to do 

sudo mv /root/oldmacfiles ~/desktop/

then I used the lowercase d instead of upper case which made a new folder in the home folder, which isn't where I was looking... 

so after that followed the remaining codes
and this is the file permissions now


-rwx------ 1 constellanation constellanation   65076 2011-02-09 19:29 P1010021.jpg


the only small difference for anyone looking at this in the future, is the folder is still protected, but you can take it out of the folder fine.

---

### Post by robsoles on 2011-02-09
> **jroa said:**
> Have you tried using the asterisk with the directory name?

```
mv *originaldirectory* newdirectory*
```

That implementation of the asterisk will cause every directory that starts with 'originaldirectory' to be moved (or at least considered to move by the system).

'mv' doesn't use the '-R' (recursive) switch that 'cp' and others use, that is because if you are moving a directory then it implies that you are moving it's contents (especially subfolders) along with it - it is unusual that the error said 'directory is not empty' unless it was referring to your proposed destination already containing a folder with the same name as the folder you were moving.

Please consider marking your thread as solved.

---

### Post by constellanation on 2011-02-09
Marked as solved, you're a genius.

so i figured out what my actual mistake was following your directions (for those keeping count, atleast 3)

I was logged in as root in the terminal so when following your directions I was creating new folders in root, not on my desktop.

I was trying with little pieces of the data (instead of possibly losing everything at once) and then couldn't get it to work again.  But after a minute of messing around nautilus I saw the differences in the two paths.  And voila, it worked like a charm!

Thank you again!

---

### Post by asmoore82 on 2011-02-10
You should never `chmod -R` in combination with number codes such as `700`.

Ordinary files should not have executable permissions.
The only proper forms of `chmod -R` are with the letter codes such as `+rwX`.
Note the capital `X` - this means execute only on folders and executables.

To repair improper permissions after a `chmod -R 700`, you could do this:
```
find */repair/this/folder* -type f -print0 | xargs -0 chmod -x
```
^This removes the execute permission from plain files but leaves it on folders.

---

### Post by robsoles on 2011-02-10
I was just cutting to the chase for constellanation, if they had an actual malicious binary and managed to execute it after I advised to just nail the lot with '700' I would be mortified but I would also be shocked speechless. With data from six years ago on an apple system I would be more than stunned to learn that constellanation took the other steps necessary to execute a malicious binary without knowingly 'starting' the binary from terminal or nautilus.

I've never had a problem with random files having the execute bit set - sure it isn't a technically correct way to keep 'non-executables' but I sure do challenge anybody to get themselves a problem by such files having execute permissions without writing their name **./like-this** (or another fairly specific way) into terminal; if you double click a text file with execute permissions in nautilus you will be asked: Do you want to display the contents or execute it. Movies open the media player, so does Audio.

I can't say that I've double clicked (or used a specific name in terminal for) a 'source' file (.c etc) that I had carelessly (but knowingly, perhaps where I should apologise to constellanation et al) set the execute bit on. Admittedly if you randomly give binaries you aren't aware of execute permissions it's an unnecessary risk, that is sure too.

Should someone in doubt be viewing the thread in the future, just grab anybody's commands for terminal and pop them into Google and read up on if people liked following the advice (which included those commands) or weren't very happy with the results they got - some or other item in the search results may explain better exactly what the commands are doing.

Another way to fix folders for read/write/execute for user and group, read-only for 'world' (Will effect all subfolders of current folder so be in the directory you want to target or specify your target folder carefully)```
find -type d -exec chmod 77[COLOR=Red]5[/COLOR] {} \;
```Another way to fix files for same minus execute:```
find -type f -exec chmod 664 {} \;
```**BUT** these, more specifically the '-type f' (files) one, are not safe to apply to anything else but a home folder (or at least a folder that no binary you wish to execute resides in), preferably do it to yourself: ~/

You can replace everything between '-exec' and ';' on the line to have whatever you like done to the files, have a care and set up a dummy subfolder with dummy targets to test your 'happiness' on before you do it to anything you care about though.

---

### Post by asmoore82 on 2011-02-10
As Desktop Linux continues its growth, the attacks are inevitable.
We've been touting the advanced security for years, the time to prove it will come.
Fixing problems before they cause a problem is the way to go - and it's Free.

> **robsoles said:**
> ```
find -type d -exec chmod 774 {} \;
```Another way to fix files for same minus execute:```
find -type f -exec chmod 664 {} \;
```

That first `find ... chmod` should be 775 instead of 774.

---

