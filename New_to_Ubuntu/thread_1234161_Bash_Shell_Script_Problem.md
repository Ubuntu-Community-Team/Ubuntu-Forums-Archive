---
title: "Bash Shell Script Problem"
date: 2009-08-07
forum: New to Ubuntu
---

### Post by DanYoSon on 2009-08-07
I am working on my first Shell Script. it is a backup script that backs up to a usb drive. 

i want it to make sure that the drive is mounted at the beginging of the script so i am useing this 

```
mount_check=mount | grep /dev/sdb1
if $mount _check == /dev/sdb1*
then echo mount successful
else mount -t vfat /dev/sdb1 /mnt/usb_1
fi

```but when i run it i get the error 
mount_check command does not exist. what am i doing wrong i beleve it to be a syntax error that my inexperience is causing.

thanks

---

### Post by Dark006 on 2009-08-07
Why not just add the flash drive to your /etc/fstab?? Thats what I did and it works great. I would recommend getting the UUID by running
```
blkid
```
and then picking your flash drive. Then copy that UUID and add it to your /etc/fstab  like this (this is mine for example).
```
UUID=2afd3a4a-a880-469d-85de-a67d8e3d91ba /media/backup ext3 rw 0 0
```

---

### Post by bodhi.zazen on 2009-08-07
I think your syntax is off a bit.

Put your command in either single tics ` ` or ()[FONT=monospace]

[/FONT]mount_check=`mount | grep /dev/sdb1`[FONT=monospace]
[/FONT]mount_check=(mount | grep /dev/sdb1)[FONT=monospace]

[/FONT]Second, your if syntax is not the best. /dev/sdb can be variable depending on if you have various removable devices attached. Better to check via label or uuid.

here is a snipit for testing :[FONT=Verdana]

[/FONT][FONT=Verdana][COLOR=#000000]if [ "$(whoami)" != 'root' ]; then

Or this :

```
test "$(mount_check)" != '/dev/sdb1' && (echo "/dev/sbd1 is not mounted; mount /dev/sdb1)
```
[/COLOR]Or shortened ```
[/FONT][FONT=Verdana][COLOR=#000000]test "$(mount_check)" != '/dev/sdb1' && mount /dev/sdb1
```

[/COLOR][/FONT]

---

### Post by lswb on 2009-08-07
In addition to the previous comments, there is also a "mountpoint" command that tells if a particular directory is a mountpoint or not, for example

```

$ mountpoint /
/ is a mountpoint
$ mountpoint /etc
/etc is not a mountpoint

```
(returns 0 if mountpoint, non-zero if not)

---

### Post by DanYoSon on 2009-08-07
thanks guys turns out i left out the #!bin/sh at the top of the file thinking that it was a comment in the example i was reading. but your other suggestions helped.

question though why is 

```
#!bin/sh 
```not a comment even though it starts with a comment symbol??

thanks

---

### Post by Liolikas on 2009-08-07
It is comment.
But also it tells to Linux system in which language script is:
sh
bash
perl
python
etc.

If there is no this line you still can run it with:
sh script_name
Command.

---

### Post by DanYoSon on 2009-08-07
ok that makes sense 

another question i have to segments of code in the same shell script and they look identical but one works and the other doesnt

```
find_usb ()
{
#Find USB location
location_1_1='vol_id --uuid /dev/sdb1'
location_1_2='vol_id --uuid /dev/sdb2'
location_2_1='vol_id --uuid /dev/sdc1'
location_2_2='vol_id --uuid /dev/sdc2'
location_3_1='vol_id --uuid /dev/sdd1'
location_3_2='vol_id --uuid /dev/sdd2'
if $location_1_1 == DC2C-D7C6
        then location=1
elif $location_1_2 == DC2C-D7C6
        then location=2
elif $location_2_1 == DC2C-D7C6
        then location=3
elif $location_2_2 == DC2C-D7C6
        then location=4
elif $location_3_1 == DC2C-D7C6
        then location=5
elif $location_3_2 == DC2C-D7C6
        then location=6
else
        echo "USB not NOT pluged in! Backup FAILED!"
exit
fi
if $location == 1
        then mount_loc="/dev/sdb1"
elif $location == 2
        then mount_loc="/dev/sdb2"
elif $location == 3
        then mount_loc="/dev/sdc1"
elif $location == 4
        then mount_loc="/dev/sdc2"
elif $location == 5
        then mount_loc="/dev/sdd1"
elif $location == 6
        then mount_loc="/dev/sdd2"
fi
}
```works

```
check_mount ()
{
status='vol_id --uuid /dev/sdb1'
echo $status
}
```doesnt execute the command just displays the text looks the same to me.

---

### Post by asmoore82 on 2009-08-07
Bash scripting, probably all shell scripting, is a very strange animal ... at first.

Your first problem is the "if" statement syntax.

In shell scripting, "if" tests the exit status of an arbitrary command, so a "naked" conditional test
is meaningless, you need to explicitly use the "test" keyword or better still, for clarity,
use a [ ... ] construct which is a synonym for "test"
Often, you will also see and probably should, again for clarity, explicitly terminate the test with a `;`

Your 2nd problem is if you want to use the ` ... ` syntax for command substitution,
you have use "back-ticks," not single quotes. It's usually the tilde key beside the
1 and above the tab key. I would recommend forgoing that altogether and using
the $( ... ) syntax, which does the same thing.

A fully corrected version of your OP:
```
mount_check=mount | grep /dev/sdb1
if $mount _check == /dev/sdb1*
then echo mount successful
else mount -t vfat /dev/sdb1 /mnt/usb_1
fi
```
could look like this:
```
if mount | grep /dev/sdb1; then
   echo "It appears /dev/sdb1 is already mounted."
else
   mount -t vfat /dev/sdb1 /mnt/usb_1
fi
```

---

### Post by lswb on 2009-08-07
> **DanYoSon said:**
> ok that makes sense 

another question i have to segments of code in the same shell script and they look identical but one works and the other doesnt

```
find_usb ()
{
#Find USB location
location_1_1='vol_id --uuid /dev/sdb1' # use backticks ` or preferably
location_1_2='vol_id --uuid /dev/sdb2' # surround statement with $( )
location_2_1='vol_id --uuid /dev/sdc1' #i.e. loc="$(vol_id --uuid /dev/sdx)"
location_2_2='vol_id --uuid /dev/sdc2'
location_3_1='vol_id --uuid /dev/sdd1'
location_3_2='vol_id --uuid /dev/sdd2'
if $location_1_1 == DC2C-D7C6       # tests for string equality 
        then location=1             # must be inside [ ] with space 
elif $location_1_2 == DC2C-D7C6     # after [ and before ], (or use "if test ...")
        then location=2             # and quoting of variables and
elif $location_2_1 == DC2C-D7C6     # string literals is usually 
        then location=3             # good practice, like this:
elif $location_2_2 == DC2C-D7C6   # if [ "$var" == "string" ]
        then location=4
elif $location_3_1 == DC2C-D7C6
        then location=5
elif $location_3_2 == DC2C-D7C6
        then location=6
else
        echo "USB not NOT pluged in! Backup FAILED!"
exit
fi
if $location == 1  # again, no brackets
        then mount_loc="/dev/sdb1"
elif $location == 2
        then mount_loc="/dev/sdb2"
elif $location == 3
        then mount_loc="/dev/sdc1"
elif $location == 4
        then mount_loc="/dev/sdc2"
elif $location == 5
        then mount_loc="/dev/sdd1"
elif $location == 6
        then mount_loc="/dev/sdd2"
fi
}
```works

```
check_mount ()
{
status='vol_id --uuid /dev/sdb1' # use backticks ` or $(statement) form
echo $status
}
```doesnt execute the command just displays the text looks the same to me.

Does it really work? I've put comments in the code with the problems I see. A really good reference on bash programming is 

[http://tldp.org/LDP/abs/html/](http://tldp.org/LDP/abs/html/)
and be sure to check the parent sites of this same url for lots of other good info.

---

### Post by asmoore82 on 2009-08-07
^^notice that once you have the proper syntax,
you can do a lot of condensing and work smarter, not harder.

this:
```
mount_check=mount | grep /dev/sdb1
if $mount _check == /dev/sdb1
then
```
cat become this:
```
if mount | grep /dev/sdb1; then
```

likewise, this:
```
location_1_1='vol_id --uuid /dev/sdb1'
if $location_1_1 == DC2C-D7C6
then location=1
fi
if $location == 1
then mount_loc="/dev/sdb1"
fi
```
can become this:
```
if [ $( vol_id --uuid /dev/sdb1 ) = "DC2C-D7C6" ]; then
   mount_loc="/dev/sdb1"
fi
```

**Very Important!!**
Notice in this last example, you can also drop the usage of `==` in favor of just `=`
In practice, I've never seen `==` in a shell script and did not know it existed until now.

Your logic is pretty good, you are just running into all of the common scripting errors;
good programmers have gotten used to computers as "number crunchers" but shell scripting
turns that good practice on its head; shells are the best "text crunchers."
So, when you really want number comparisons, use should explicitly use `test` switches:
-eq, -ne, -lt, -gt :: equal(==), not equal(!=), less than(<), greater than(>)

Another side effect of the "text crunching" mentality is double quotes everywhere!

Examples: `=` for text; `-eq` for numbers
```
**asmoore@ubuntu-lenovo:~$** test "yes" = "yes" && echo true
true
**asmoore@ubuntu-lenovo:~$** test "yes" = "no"  && echo true
**asmoore@ubuntu-lenovo:~$** test "1" -eq "1"   && echo true
true
**asmoore@ubuntu-lenovo:~$** test "1" -eq "0"   && echo true
**asmoore@ubuntu-lenovo:~$** test "1" = "1"     && echo true
true
[COLOR="Red"]**asmoore@ubuntu-lenovo:~$** test "1" = " 1 "   && echo true[/COLOR]
[COLOR="Red"]**asmoore@ubuntu-lenovo:~$** test "01" = "001"  && echo true[/COLOR]
**asmoore@ubuntu-lenovo:~$** test "01" -eq "1"  && echo true
true
```

Note the ones in [COLOR="Red"]Red[/COLOR] that don't work as expected,
because of the text vs. numbers difference

Examples: [ ... ] is the same as `test`
```
**asmoore@ubuntu-lenovo:~$** [ "yes" = "yes" ] && echo true
true
**asmoore@ubuntu-lenovo:~$** [ "yes" = "no" ]  && echo true
**asmoore@ubuntu-lenovo:~$** [ "1" -eq "1" ]   && echo true
true
**asmoore@ubuntu-lenovo:~$** [ "1" -eq "0" ]   && echo true
**asmoore@ubuntu-lenovo:~$** [ "1" = "1" ]     && echo true
true
[COLOR="Red"]**asmoore@ubuntu-lenovo:~$** [ "1" = " 1 " ]   && echo true[/COLOR]
[COLOR="Red"]**asmoore@ubuntu-lenovo:~$** [ "01" = "001" ]  && echo true[/COLOR]
**asmoore@ubuntu-lenovo:~$** [ "01" -eq "1" ]  && echo true
true
```

---

### Post by DanYoSon on 2009-08-08
thanks guys this has been a big help i have downloaded that tutorial.

---

