---
title: "how do I get things to go to the partition I want them on automatically?"
date: 2010-02-18
forum: New to Ubuntu
---

### Post by hortstu on 2010-02-18
When I reinstalled a few days ago I partitioned with a separate data partition.  

First I realized I wasn't considered the owner of the partition so I think I changed that with a 

```
chown -R username:username files to own
```

However it seems like everything is automatically being saved to the 3 gb / partition... or the /home partition, not sure.  Anyway don't I want all my settings, docs, pics, and music automatically going to the data file?

---

### Post by nothingspecial on 2010-02-18
> **hortstu said:**
> When I reinstalled a few days ago I partitioned with a separate data partition.  

First I realized I wasn't considered the owner of the partition so I think I changed that with a 

```
chown -R username:username files to own
```

However it seems like everything is automatically being saved to the 3 gb / partition... or the /home partition, not sure.  Anyway don't I want all my settings, docs, pics, and music automatically going to the data file?

You want your settings in your /home partition. You want any binaries and system wide config files in your / partition.

You should be able to choose where to save pics, docs and music with whatever application you are using to save them.

---

### Post by mikewhatever on 2010-02-18
> **hortstu said:**
> ...........

However it seems like everything is automatically being saved to the 3 gb / partition... or the /home partition, not sure.  Anyway don't I want all my settings, docs, pics, and music automatically going to the data file?

You don't have much choice about settings, but docs, pictures and music don't go anywhere automatically. You have to be downloading or creating them, and you choose where to save them.

---

### Post by hortstu on 2010-02-18
so all the changes I've made are going into the separate partition so in the event that I need to reinstall hardy will already be setup the way I like it?

---

### Post by Elisabete on 2010-02-18
Hello, 

I'm also new to Ubuntu and had to figure this out the other day. I wrote up the instructions I had adapted from other online resources and sent them out to my class mates (I'm a CS undergrad). Thought I'd post them here as well, as they might be useful to others as well. 

Enjoy,
Elisabete

---

  	 	 	 	 	 	  [FONT=Verdana, sans-serif][SIZE=2][B]How to designate which OS your dual boot defaults to

[/B][/SIZE][/FONT]
 [FONT=Verdana, sans-serif][SIZE=2]So, you&#8217;ve just portioned your hard drive and installed Ubuntu to the new partition. When you reboot your computer, you come to boot menu where you are given the choice of which OS you want to boot into. Ha, but you didn&#8217;t act fast enough and now you&#8217;re booting into Ubuntu. That&#8217;s because Ubuntu has been set as your default OS. 

How do you change it, you ask? By following the steps below![/SIZE][/FONT]
 
[LIST=1]
[*][FONT=Verdana, sans-serif][SIZE=2]Boot 	into Ubuntu
[/SIZE][/FONT]
	
[*][FONT=Verdana, sans-serif][SIZE=2]Open 	up the terminal (command line)[/SIZE][/FONT]
[/LIST]
 [FONT=Verdana, sans-serif][SIZE=2][B]Applications -> Accessories -> Terminal
[/B][/SIZE][/FONT]

 
[LIST=1]
[*][FONT=Verdana, sans-serif][SIZE=2]Within 	the terminal window, type:[/SIZE][/FONT]
[/LIST]
 [FONT=Verdana, sans-serif][SIZE=2]**gksudo gedit /etc/default/grub**[/SIZE][/FONT]
 [FONT=Verdana, sans-serif][SIZE=2]You will be prompted for your admin password. After the password is accepted a new window will open with code displayed. 
[/SIZE][/FONT]

 
[LIST=1]
[*][FONT=Verdana, sans-serif][SIZE=2]Find 	the line of code that reads:
          [/SIZE][/FONT][B][FONT=Verdana, sans-serif][SIZE=2]GRUB_DEFAULT=0
[/SIZE][/FONT][/B][B][FONT=Verdana, sans-serif][SIZE=2]This 	is the line you&#8217;re going to need to change
[/SIZE][/FONT][/B]
	
[*][FONT=Verdana, sans-serif][SIZE=2]Open 	a new Terminal Window and type the following command:
[/SIZE][/FONT][FONT=Courier New, monospace][SIZE=2][SIZE=2] 		[/SIZE][/SIZE][/FONT][FONT=Courier New, monospace][SIZE=2][FONT=Verdana, sans-serif][SIZE=2]**grep menuentry /boot/grub/grub.cfg**[/SIZE][/FONT][/SIZE][/FONT][FONT=Verdana, sans-serif][SIZE=2]
This 	will now display your boot menu. Look for the name of the OS you&#8217;d 	like to set as your default. Highlight the entire string (quotes and 	all), right click and copy. 
[/SIZE][/FONT]
	
[*][FONT=Verdana, sans-serif][SIZE=2]Return 	to the window which contains the program code, right click and paste 	the string directly after the default command. Here is an example of 	what it should look like...
 	[/SIZE][/FONT]**[FONT=Verdana, sans-serif][SIZE=2]GRUB_DEFAULT=[/SIZE][/FONT]**[SIZE=2] 	[/SIZE][FONT=Courier New, monospace][SIZE=2][FONT=Verdana, sans-serif][SIZE=2][B]"Windows 	Vista (loader) (on /dev/sdal)"
[/B][/SIZE][/FONT][/SIZE][/FONT][FONT=Courier New, monospace][SIZE=2][FONT=Verdana, sans-serif][SIZE=2]My 	example lists Vista as the default, but you can of course choose any 	OS. 
[/SIZE][/FONT][/SIZE][/FONT]
	
[*][FONT=Courier New, monospace][SIZE=2][FONT=Verdana, sans-serif][SIZE=2]Save 	the program (File -> Save) and close the window. Now return to 	your original Terminal Window and type:
 	[/SIZE][/FONT][/SIZE][/FONT][FONT=Courier New, monospace][SIZE=2][FONT=Verdana, sans-serif][SIZE=2][B]sudo 	update-grub
[/B][/SIZE][/FONT][/SIZE][/FONT][FONT=Courier New, monospace][SIZE=2][FONT=Verdana, sans-serif][SIZE=2]You&#8217;ll 	be prompted for your admin password again. Type carefully in the 	terminal as you won&#8217;t see what you&#8217;re typing. 
[/SIZE][/FONT][/SIZE][/FONT]
	
[*][FONT=Courier New, monospace][SIZE=2][FONT=Verdana, sans-serif][SIZE=2]If 	it worked, some additional lines will be printed, ending in &#8220;done&#8221;. 	Close out of everything and reboot to see if it worked! [/SIZE][/FONT][/SIZE][/FONT] 	
[/LIST]

---

### Post by oldfred on 2010-02-18
More info on shared data partitions.

Share Windows partition:
[http://lifehacker.com/348858/use-a-single-data-store-when-dual-booting](http://lifehacker.com/348858/use-a-single-data-store-when-dual-booting)
Share data partition
[http://blog.linuxtoday.com/blog/2009/08/painless-linux.html](http://blog.linuxtoday.com/blog/2009/08/painless-linux.html)

I created a data partition and put all my data folders from home from my old install into data. I then deleted the folders (empty) in my new install and linked to the folders in the data partition. My mount in fstab was /usr/local/fred/data so I would not see the data partition in Nautilus except thru the links. See link above and some of the posts in the link (painless..)

from home I then linked in the data folders:
ln -s /usr/local/fred/data/Music
ln -s /usr/local/fred/data/Videos
etc

---

