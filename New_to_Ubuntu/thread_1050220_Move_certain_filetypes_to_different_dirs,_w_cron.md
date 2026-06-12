---
title: "Move certain filetypes to different dirs, w cron?"
date: 2009-01-25
forum: New to Ubuntu
---

### Post by d3adpool on 2009-01-25
I've looked around at a few places and thought I'd post here after I've poked around a bit to find my own answer... so here it goes:

I'd like to set a cron for x number of minutes to poll a directory copy all pictures to a certain dir, mp3's to another and unpack any zip, rar ect files... even as far as ones buried in folders and then delete the whole mess once everything's been moved out of my upload dir.

I know ubuntu can do it, just not sure how to go about finding the answer out for myself.

Thanks for reading.

---

### Post by blueridgedog on 2009-01-25
This is possible with shell scripting, but the unzipping process would be advanced.  I think it would be about a half day's work to get it setup and debugged, but it would be a great project for you to learn shell scripting.

For example.  To move all MP3's from one directory to another cold be a simple script such as:

```
#!/bin/bash
cd /my/directory
rename 'y/MP /mp./' *
mv *.mp3 /my/newdirectory
```

You could save this as "movefiles.sh"

Cron can be told to run it via:

sudo crontab -e

Then entering a line such as:

```
0,10,20,30,40,50 *     *     *     *         /path/to/my/movefiles.sh 
```

This basically means run this every 10 minutes of every hour of every day of the month of every month and on all seven of the days of the week.

See [http://www.adminschoice.com/docs/crontab.htm](http://www.adminschoice.com/docs/crontab.htm) for more information on the format of the crontab file.

Be certain to test your scripts before trying to put them into cron and welcome to bash shell scripting!  It is a powerful tool.

---

### Post by sdennie on 2009-01-25
As stated above, the crontab is really the only confusing part.  A slightly shorter way to specifiy your crontab would be:

```

*/10 * * * * command

```

That means "every ten minutes".

The other thing you are going to find useful is find.  For example, to find all .zip files even if they are in subdirectories use:

```

find /path/to/files -type f -name "*.zip"

```

The syntax to unzip them once they are found will probably be something like:

```

find /path/to/files -type f -name "*.zip" -exec unzip {}\;

```

---

