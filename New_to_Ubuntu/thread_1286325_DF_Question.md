---
title: "DF Question"
date: 2009-10-08
forum: New to Ubuntu
---

### Post by Marko723 on 2009-10-08
Is there a way to edit the order in which 'df' displays the mount points?

A few weeks back I re-partitioned and formatted some drives and they are not in the numerical order as they are labeled.  Originally everything was in numeric order, but as you can see below, Drive WD_1 is 2nd from last.  Can this be adjusted somehow?  I know it's only cosmetic, but it's been bugging me for a while now.

Thanks
Mark  

```
[SIZE="2"]Filesystem         1024-blocks      Used Available Capacity Mounted on
/dev/sda1            474781296 147064656 303599064      33% /
tmpfs                  1030832         0   1030832       0% /lib/init/rw
varrun                 1030832       604   1030228       1% /var/run
varlock                1030832         0   1030832       0% /var/lock
udev                   1030832       180   1030652       1% /dev
tmpfs                  1030832         0   1030832       0% /dev/shm
lrm                    1030832      2192   1028640       1% /lib/modules/2.6.28-15-generic/volatile
/dev/sdc1            1442145212    202364 1368686048       1% /mnt/WD_2
/dev/sdd1            1442145212    202364 1368686048       1% /mnt/WD_3
/dev/sde1            1442145212    202364 1368686048       1% /mnt/WD_4
/dev/sdb1            1442145212 615914676 752973736      45% /mnt/WD_1
/dev/sdf1            1442145212 500287556 868600856      37% /mnt/WD_5[/SIZE]
```

---

### Post by unutbu on 2009-10-08
Perhaps try
```

df | sort 

```

---

### Post by Marko723 on 2009-10-08
> **unutbu said:**
> Perhaps try
```

df | sort 

```

Thanks,  but I was hoping for a solution to correct the display when I use; 
```
df -h
```

Perhaps I need to umount and mount in that specific order?  or is there a file I can edit?

---

### Post by drs305 on 2009-10-08
Same thing. Take unutbu's command and put it in your ~/.bashrc file as an alias so anytime you type "df" it automatically does the sort for you.

> alias df='df -h | sort'

Close your terminal or run "source .bashrc" to refresh and enable it.

---

### Post by Marko723 on 2009-10-08
What I was hoping for was to return the display to;
```
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             453G  121G  310G  29% /
tmpfs                1007M     0 1007M   0% /lib/init/rw
varrun               1007M  1.2M 1006M   1% /var/run
varlock              1007M     0 1007M   0% /var/lock
udev                 1007M  160K 1007M   1% /dev
tmpfs                1007M     0 1007M   0% /dev/shm
lrm                  1007M  2.2M 1005M   1% /lib/modules/2.6.28-15-generic/volatile
/dev/sdb              1.4T  417G  889G  32% /mnt/WD_1
/dev/sdc              1.4T  198M  1.3T   1% /mnt/WD_2
/dev/sdd              1.4T  198M  1.3T   1% /mnt/WD_3
/dev/sde              1.4T  198M  1.3T   1% /mnt/WD_4
/dev/sdf              1.4T  308G  999G  24% /mnt/WD_5
```

The |sort messes up the logical partitions, which usually nest under dev/sda
But if it can't be done...

---

### Post by unutbu on 2009-10-08
Save this as ~/bin/mydf
[PHP]
#!/usr/bin/env python
from subprocess import Popen,PIPE
proc=Popen('df -h', shell=True, stdout=PIPE, )
output=proc.communicate()[0]
result=[]
mnts=[]
for line in output.splitlines():
    fields=line.split()
    if fields[-1].startswith('/mnt'):
        mnts.append(line)
    else:
        result.append(line)
mnts.sort()
print('\n'.join(result))
print('\n'.join(mnts))
[/PHP]

Make it executable:
```

chmod +x ~/bin/mydf

```
Run it like this:
```

mydf
```

---

### Post by Marko723 on 2009-10-08
> **unutbu said:**
> Save this as ~/bin/mydf
[PHP]
#!/usr/bin/env python
from subprocess import Popen,PIPE
proc=Popen('df -h', shell=True, stdout=PIPE, )
output=proc.communicate()[0]
result=[]
mnts=[]
for line in output.splitlines():
    fields=line.split()
    if fields[-1].startswith('/mnt'):
        mnts.append(line)
    else:
        result.append(line)
mnts.sort()
print('\n'.join(result))
print('\n'.join(mnts))
[/PHP]

Make it executable:
```

chmod +x ~/bin/mydf

```
Run it like this:
```

mydf
```

Cool... Thank You.

I'll give that a try tomorrow after work.

---

### Post by Marko723 on 2009-10-10
Just an update:  The easiest thing I found was to 1 by 1  "umount" the drives that were out of order, and then run a ```
mount -a
``` now everything is back in other order.  I guess the display order is set by the order in which you add drives to the system, so it might be time stamp related.

Thanks to everyone for their replies before.

---

### Post by scorp123 on 2009-10-10
And why not specify the order yourself?
```

> df -h /dev/sda1 /dev/sdb1 /dev/sda2 /dev/sda9 /dev/sda7 /dev/sda11

Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             130M   20M  104M  16% /boot
/dev/sdb1             587G  534G   51G  92% /data
udev                  3.9G  236K  3.9G   1% /dev
/dev/sda9             8.0G  147M  7.4G   2% /tmp
/dev/sda7             3.5G  715M  2.6G  22% /var
/dev/sda11            543G  182G  359G  34% /home
```

---

### Post by scorp123 on 2009-10-10
And if you want certain filesystem types excluded you can use the appropriate paramters for this, as per manual (man df)

```
df -hl -x tmpfs -x udev
```

---

### Post by Marko723 on 2009-10-10
[QUOTE=scorp123;8082955]And why not specify the order yourself?

Good question, I guess I never really looked in to it that deep, and old habits don't die quickly.  

It comes down to the fact that I need to invest more time in to working with the OS.  Right now it's a bit of a hobby which I spend time with here and there on the weekend. The unfortunate part is that I tend forget some of the things I've modified in the past, so I guess I'm going to have to start keeping a diary of changes I've made.

I'm just really glad there is such a supportive community out there in which the members pitch in to help out us newbies 

Mark

Edit: My over all objective is to remote admin server via command line.  I've set up an old p4 box in the back corner of the basement, with Samba and hope to stream video off it with a WDTV or Asus O!Play.  There is no monitor, and I'm doing everything over SSH.  It just makes it easier for myself to be able to SSH in every now and then to check drive space.  If I need to shuffle things around I would sooner do it over SSH oppose to Windows GUI.  Having the drives show up in a particular order just better fits the picture in my mind's eye.

---

### Post by scorp123 on 2009-10-10
> **Marko723 said:**
>  The unfortunate part is that I tend forget some of the things I've modified in the past I had the same problem when I started with Linux back in 1996 .... My solution? Participate in mailing lists or --which is more common today-- participate on Linux forums and help other people solve their problems. That's the best "Linux training" you can get. The cool thing being that forums such as this very forum right here allow you to subscribe to threads, group those subscribed threads into categories (e.g. I have a thread category "Network Problems", then "Virtualisation", then "Advanced System Administration", "Shell Scripting", and so on) ... and lo' and behold: You get your own personalised collection of articles and threads that match your interests. The search function solves the rest.

So later on, when you run into a problem with "df" again, you simply search your collection of subscribed threads about "df" ... and taddaaa. You find this thread again. Problem solved. Again.


> **Marko723 said:**
>   so I guess I'm going to have to start keeping a diary of changes I've made.  Many people start a blog for this reason. Or they join a "Linux fan" group on Facebook or something like that. So you can write down your experiences and later if ever needed find your own texts again.

> **Marko723 said:**
>  It just makes it easier for myself to be able to SSH in every now and then to check drive space. ...  Having the drives show up in a particular order just better fits the picture in my mind's eye.
Well, if that's the case you might be interested in this little "trick" I did for one of my own systems ... I use it as "Torrent Downloader". So there is an Apache web server on that machine, there is "torrentflux" (a web based BitTorrent program) on top of that ... And so, while I am in the office (where we block all P2P traffic due to security reasons) or at customers I can remotely connect to my small "torrentflux" server at home and tell it to download all the latest and greatest Linux, BSD and OpenSolaris ISO's while I am at work ... and in the evening when I get home my little box is full of new stuff I can play with.

Of course ... the disk gets full over time. And sometimes I login via SSH, I do "apt-get update" and "dist-upgrade" and what not but for the life of me I sometimes simply forget to check if there is enough disk space left ....

So for me the ideal solution would be if the system simply told me about the disk space when I login.

Maybe you would like to do the same?

To get this working please open your **".bashrc**" file in an editor (you said you wanted that on a server ... so you could open your _local_ **.bashrc** and then simply ***scp*** it over to the server ...). Please enter the following shell command:
```
gedit /home/YourUserNameHere/.bashrc
```

And now go to the end of the file ... hit the "Enter" key a few times so we get a bit of space and then add these lines to the bottom of the file (please copy & paste):

```

echo
echo "                                  \\\\\|///"
echo "                                \\\\  ~ ~  //"
echo "                                 (  @ @  )"
echo "-------------------------------oOOo-(_)-oOOo-----------------------------------"
echo
/usr/bin/top -b -n1 | /usr/bin/head -n5
echo
#
# Add the mount points you're interested in
# to the "df" command below,
# and put them in the order you want them
# 
/bin/df -hT / /home /data /opt
echo
echo "----------------------------------------Oooo.----------------------------------"
echo "                              .oooO     (   )"
echo "                              (   )      ) /"
echo "                               \ (      (_/"
echo "                                \_)"
echo

```

[B][U]
Result:[/U][/B]

Now everytime you login, you should get a message like this right before the shell prompt appears:
```

                                  \\\|///
                                \\  ~ ~  //
                                 (  @ @  )
-------------------------------oOOo-(_)-oOOo-----------------------------------

top - 20:47:45 up 10:12,  4 users,  load average: 0.08, 0.08, 0.08
Tasks: 184 total,   1 running, 183 sleeping,   0 stopped,   0 zombie
Cpu(s):  2.4%us,  0.5%sy,  0.2%ni, 96.5%id,  0.4%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:   8083176k total,  7656704k used,   426472k free,   174808k buffers
Swap: 17864240k total,        0k used, 17864240k free,  6540964k cached

Filesystem    Type    Size  Used Avail Use% Mounted on
/dev/sda5     ext4    2.4G  252M  2.0G  12% /
/dev/sda11    ext4    543G  182G  359G  34% /home
/dev/sdb1     ext4    587G  534G   51G  92% /data
/dev/sda8     ext4    6.9G  289M  6.3G   5% /opt

----------------------------------------Oooo.----------------------------------
                              .oooO     (   )
                              (   )      ) /
                               \ (      (_/
                                \_)
```


This works tip top in a funny charming way :D


BTW ... On my systems I reduced the contents of these files to a minimum (i.e. I did not delete them but pretty much deleted their content):
- **/etc/motd**
- **/etc/motd.tail**

The contents of those files will be displayed too when you login. Usually it just contains the legal "bla bla bla" about Ubuntu coming without warranty and what not. It's not really interesting and just makes more and more stuff be displayed on-screen when you login. So to reduce the clutter on the screen you could empty those two files.


And while we're at it .... Another stupid trick I did on another system involves the program "cowsay" (it's not installed by default). The program does what it says: It will display a cow that says whatever you want it to say. So this little command ...
```
cowsay -s -W 70 `/usr/bin/top -b -n1 | /usr/bin/head -n5`
```

Will give this result:
```
 __________________________________________________________________
/ top - 20:56:01 up 10:20, 4 users, load average: 0.07, 0.06, 0.07 \
| Tasks: 185 total, 1 running, 184 sleeping, 0 stopped, 0 zombie   |
| Cpu(s): 2.3%us, 0.5%sy, 0.2%ni, 96.5%id, 0.4%wa, 0.0%hi, 0.0%si, |
| 0.0%st Mem: 8083176k total, 7656072k used, 427104k free, 175832k |
| buffers Swap: 17864240k total, 0k used, 17864240k free, 6540996k |
\ cached                                                           /
 ------------------------------------------------------------------
        \   ^__^
         \  (**)\_______
            (__)\       )\/\
             U  ||----w |
                ||     ||
```

So that would be another funny command line you could put into a ".bashrc" file if you want :D  (please note that you should then remove the "top" command from the other example if you add both to the same ".bashrc" as displaying the "top" output twice would be redundant)

Have fun :)

---

### Post by Marko723 on 2009-10-10
> **scorp123 said:**
> I had the same problem when I started with Linux back in 1996 .... My solution? Participate in mailing lists or --which is more common today-- participate on Linux forums and help other people solve their problems. That's the best "Linux training" you can get. The cool thing being that forums such as this very forum right here allow you to subscribe to threads, group those subscribed threads into categories (e.g. I have a thread category "Network Problems", then "Virtualisation", then "Advanced System Administration", "Shell Scripting", and so on) ... and lo' and behold: You get your own personalised collection of articles and threads that match your interests. The search function solves the rest.

Have fun :)

WOW, that stuff you posted is so cool!  I've got this message book marked so I can come back and try your suggestions.

I used to work on HP-UX many many many (Did I mention it was a long time ago?) years ago, moved on to Enterprize network security and design.  About 9 years ago I've changed roles again to move into IT control auditing and have been hands off ever since.  Microsoft has truely ticked me off and I've made the jump on 2 of my home computers to Lunix.  I wish I could spend more time, as I did in my early days, but with 2 young kids free time is a luxury right now, so I do what I can and 'keep moving forward'.

Thanks again for your message, it looks like some really usefull scripting!

Mark

Edit: Just to show you how dated I am, my perfered editor is vi, I know there are better after poking around on the forums, but I learned it a long time ago and it wasn't hard to pick it back up when I started modding this system.

---

### Post by scorp123 on 2009-10-10
> **Marko723 said:**
> Just to show you how dated I am, my perfered editor is vi  Mine too! 8)

Since you're a "vi" lover, you should get the package with the bells and whistles .... The default package of "vi" Ubuntu ships with is unfortunately a rather crippled version: **"vim-tiny"** 

So to get the real thing  ... read here:
[http://ubuntuforums.org/showpost.php?p=4255592&postcount=5](http://ubuntuforums.org/showpost.php?p=4255592&postcount=5)

(And yes, I just pulled that link from my "Subscribed Threads" collection ... as you can see, this method works tip top and I can easily find stuff again I wrote 1 year ago, so I don't have to fill the forum's database by writing the same stuff twice ... O:)  )

---

### Post by Marko723 on 2009-10-10
> **scorp123 said:**
> Mine too! 8)

Since you're a "vi" lover, you should get the package with the bells and whistles .... The default package of "vi" Ubuntu ships with is unfortunately a rather crippled version: **"vim-tiny"** 

So to get the real thing  ... read here:
[http://ubuntuforums.org/showpost.php?p=4255592&postcount=5](http://ubuntuforums.org/showpost.php?p=4255592&postcount=5)


Excellent!   Thank you!

Edit: just installed.  Hmmm Might have to go back to black on white.  The deep blue is hard on the eyes with a black screen and white text

---

### Post by scorp123 on 2009-10-10
> **Marko723 said:**
> The deep blue is hard on the eyes  Those colors can be customized.

[http://www.google.com/#hl=en&source=hp&q=customize+vim+syntax+highlighting&meta=&aq=0&oq=customize+vim+&fp=f6b34d33553684fe](http://www.google.com/#hl=en&source=hp&q=customize+vim+syntax+highlighting&meta=&aq=0&oq=customize+vim+&fp=f6b34d33553684fe)

---

