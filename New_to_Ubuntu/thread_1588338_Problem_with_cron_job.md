---
title: "Problem with cron job"
date: 2010-10-04
forum: New to Ubuntu
---

### Post by HighCommander540 on 2010-10-04
Hey, guys I have a script that runs a few commands and waits after each command finishes to run the next one.

It works perfectly if I manually run the script myself. But if I have cron run it the script doesn't wait it just runs all of the commands without waiting.

Here is the script. Please help me:

```

#!/bin/bash
# Script to do the daily work on the minecraft server

/usr/bin/minecraft.sh backup clean
wait $!
/usr/bin/minecraft.sh cartography
wait $!
/usr/bin/minecraft.sh logs clean
wait $!
/usr/bin/minecraft.sh restart warn
wait $!

#Make the thumbs nails for the images
php5 /var/www/minecraftMaps/create_thumbs.php

```

---

### Post by CharlesA on 2010-10-04
It should wait for the first command to finish before running the second command, unless that "wait $!" is throwing it off.

Have you tried it without that?

If that doesn't work, you could try something like this, but it would be a bit messy.

```
#!/bin/bash
/usr/bin/minecraft.sh backup clean&& /usr/bin/minecraft.sh cartography && /usr/bin/minecraft.sh logs clean && /usr/bin/minecraft.sh restart warn
```

---

### Post by HighCommander540 on 2010-10-04
> **CharlesA said:**
> It should wait for the first command to finish before running the second command, unless that "wait $!" is throwing it off.

Have you tried it without that?

If that doesn't work, you could try something like this, but it would be a bit messy.

```
#!/bin/bash
/usr/bin/minecraft.sh backup clean&& /usr/bin/minecraft.sh cartography && /usr/bin/minecraft.sh logs clean && /usr/bin/minecraft.sh restart warn
```

Yeah, I actually tried it without the wait first. That is why I added the waits. It does the same thing either way.

I found a fix for this, but it won't work for me either. My "pidof" will not show me what the process ID when i run "minecraft.sh"

What does the && do? Does it matter that the user running it is my "www-data"?

---

### Post by CharlesA on 2010-10-04
&& will run the next command after the first one successfully completes.

It would depend how you set the cronjob up, I suppose.

Does it have to run as www-data?

---

### Post by HighCommander540 on 2010-10-04
> **CharlesA said:**
> && will run the next command after the first one successfully completes.

It would depend how you set the cronjob up, I suppose.

Does it have to run as www-data?

Yes, it absolutely has to run as www-data.  Also, I tried using '&&', but it just runs the first command and none of the others.

---

### Post by CharlesA on 2010-10-04
Hrm.

Here's what one of my scripts that I run daily in cron looks like:

```
OLDDOCNAME=$(${BIN}cat ${DOCPATH}latest)
NEWDOCDIR=$DOCPATH$FOLDER
OLDDOCDIR=$DOCPATH$OLDDOCNAME
DOCLOG=${DOCPATH}log/${FOLDER}.txt

# Check if Doc is mounted and if so, do a incremental backup of it.
if ${BIN}mountpoint -q $DOCPATH
then
  { ${BIN}cp --archive --link $OLDDOCDIR $NEWDOCDIR && echo $FOLDER > ${DOCPATH}latest && ${USR}rsync --archive --itemize-changes --delete --log-file $DOCLOG $ARRAYPATH --exclude dvds --exclude lost+found $NEWDOCDIR && ${BIN}umount $DOCPATH; } 2> $ERROR || { ${BIN}cat $ERROR | ${USR}mail -s "Doc Backup failed for $DATE" $EMAIL; }
fi
```

It's messy as hell, but it gets the job done and the next command only runs after the first one completes successfully.

Have you tried grouping each command like this:

```
addgroup -gid 1004 raid || { echo "Failed to create group 'raid.'"; exit; }
```

{} runs it in the current shell, () runs it in a subshell. See [here]("http://www.gnu.org/software/bash/manual/bashref.html#Command-Grouping").

Maybe something like this:

```
{ /usr/bin/minecraft.sh backup clean; } && { /usr/bin/minecraft.sh cartography; } && { /usr/bin/minecraft.sh logs clean; } && { /usr/bin/minecraft.sh restart warn; }
```

---

### Post by HighCommander540 on 2010-10-05
Yeah, so I tried your {} thing as well. But to no avail. I don't know what is causing the problem.

It executes the first command and exits prematurely too. It only happens with cron though.

It looks like it fails when it starts here is a screen shot of top. Idk, if its an issue. But look at the process for minecraftDaily.sh...It shows up as 'minecraft.'

It has to be something with cron though. Because the script its running has a 'exit 0' status. Plus, it doesn't run the command all the way through. But if I run the script manually everything works exactly how it is supposed to.

---

### Post by CharlesA on 2010-10-05
Try piping the output to a file and see if it gives you any errors.

```
{ /usr/bin/minecraft.sh backup clean && /usr/bin/minecraft.sh cartography && /usr/bin/minecraft.sh logs clean && /usr/bin/minecraft.sh restart warn; } >> /path/to/some/file 2&>1
```

I am kinda thinking that the spaces are throwing it off.

---

### Post by anglican on 2010-10-05
> **HighCommander540 said:**
> Hey, guys I have a script that runs a few commands and waits after each command finishes to run the next one.

It works perfectly if I manually run the script myself. But if I have cron run it the script doesn't wait it just runs all of the commands without waiting.

Here is the script. Please help me:

```

#!/bin/bash
# Script to do the daily work on the minecraft server

/usr/bin/minecraft.sh backup clean
wait $!
/usr/bin/minecraft.sh cartography
wait $!
/usr/bin/minecraft.sh logs clean
wait $!
/usr/bin/minecraft.sh restart warn
wait $!

#Make the thumbs nails for the images
php5 /var/www/minecraftMaps/create_thumbs.php

```Why not specifically save the pid at the start of each process by putting something like:
```
echo $$ > /tmp/pidfile

```at the beginning (of /usr/bin/minecraft.sh). Then in your cron script read the pid:
```
pid=`cat /tmp/pidfile`
```which you can then use with:
```
wait $pid
```H

---

### Post by HighCommander540 on 2010-10-09
Yeah, I tried everything that you guys suggested. But it won't work if I run it as a cron job.

It has to be an issue with my cron. Because when its running and I look at top. The process shows up as "minecraftDaily." not "minecraftDaily.sh". And no matter what I have tried it won't work.

Maybe its because of www-data? Or did I maybe screw up the file? Is there anyway to check or fix that?

---

### Post by CharlesA on 2010-10-09
What exactly is the purpose of the script? Could you post the contents of minecraft.sh?

---

### Post by HighCommander540 on 2010-10-11
Yeah, sure I can. I don't know how it is going to help though. Because "minecraft.sh" works just fine until I try to run it with "minecraftDaily.sh", I even have it in my cron right now because the daily script won't work. Everyday I have "minecraft.sh" backup the files, make a map of the world, parse the logs, and the restart the game server.

My current cron:

```
# m h  dom mon dow   command

#Start Minecraft on Reboot
@reboot /usr/bin/minecraft.sh start

#Minecraft Daily Commands
#35 00 * * * /usr/bin/minecraftDaily.sh
6 7 * * * /usr/bin/minecraft.sh backup clean
26 7 * * * /usr/bin/minecraft.sh cartography
18 9 * * * /usr/bin/minecraft.sh logs clean
19 9 * * * /usr/bin/minecraft.sh update warn
#20 9 * * * /usr/bin/minecraft.sh restart warn

#Create Minecraft Image Thumbs
12 9 * * * php5 /var/www/minecraftMaps/create_thumbs.php

```

It works completely fine if I have the "mincraft.sh" in the cron. The problem is I want it to all work in sequence, without me having to guess how long each one takes and make the cron start the next script after I think the first one will be done.

I want it to be able to run in a script so that once one finishes the next will fire off.

Here is the script (its long):

[http://pastebin.com/APV2zScz]("http://pastebin.com/APV2zScz")

---

### Post by CharlesA on 2010-10-11
That's so confusing. It works fine with one entry per line in cron, but it won't run the script sequentially.

Try this:

```
#!/bin/bash
/usr/bin/minecraft.sh backup clean || { echo "Failed" > /home/username/mine.log 2>&1; exit; }

```

See if that runs ok with cron, then start adding the second command, see if it runs and go from there.

---

### Post by HighCommander540 on 2010-10-11
> **CharlesA said:**
> That's so confusing. It works fine with one entry per line in cron, but it won't run the script sequentially.

Try this:

```
#!/bin/bash
/usr/bin/minecraft.sh backup clean || { echo "Failed" > /home/username/mine.log 2>&1; exit; }

```

See if that runs ok with cron, then start adding the second command, see if it runs and go from there.

I know it is super confusing. It makes me angry and it makes no sense why it is doing this.

I have tried something similar to that. Already, with the "&&" when I do it that way only the first script will run.

***edit: Yeah, I just thought I would give it a try. When I use your code. The log file says "Failed." (Only with cron though I tried your code running as user and it works)**

IDK, what the problem is because what happens is all of the line sin the script fire at the same time (unless sleep is used). And when they are all running together they interfere and make it so none of the scripts do their job and end prematurely.

---

### Post by CharlesA on 2010-10-11
I didn't see anything in minecraft.sh that would start anything in the background.

Just for the hell of it, does this do anything?

```
bash /usr/bin/minecraft.sh backup clean && bash /usr/bin/minecraft.sh cartography
```

---

### Post by HighCommander540 on 2010-10-11
> **CharlesA said:**
> I didn't see anything in minecraft.sh that would start anything in the background.

Just for the hell of it, does this do anything?

```
bash /usr/bin/minecraft.sh backup clean && bash /usr/bin/minecraft.sh cartography
```

There isn't anything in there that would start it in the background. That is why I am so pissed. And even though all of the scripts run at the same time none of them work. The cartography option is supposed to start and wait for another program to finish. It does (when I just run the minecraft.sh).

Also, i tried the bash before and the same thing still happened. :(

If I watch top. What happens is minecraftDaily.sh starts and then it starts up minecraft.sh. It uses sleep and stops for like 15 seconds. Then all of the other scripts spam and then they all just stop without completing.

---

### Post by CharlesA on 2010-10-11
Sheesh! I'm out of ideas. Outside of (re)writing the script and splitting it into 4 seperate ones, that is. :(

---

### Post by HighCommander540 on 2010-10-11
> **CharlesA said:**
> Sheesh! I'm out of ideas. Outside of (re)writing the script and splitting it into 4 seperate ones, that is. :(

Damn. That is really depressing. I seriously don't understand how this is happening.

What do you mean splitting it up? Wouldn't that be just like I already have it? Running the 4 scripts at set times in cron....

---

### Post by CharlesA on 2010-10-11
Sorta. The method you've got working now would probably be better.

I was thinking of just creating 4 seperate scripts that would be run by one master script.

---

### Post by HighCommander540 on 2010-10-11
> **CharlesA said:**
> Sorta. The method you've got working now would probably be better.

I was thinking of just creating 4 seperate scripts that would be run by one master script.

Ok, well I will look into that. Because I need to find a way that doesn't exactly what the minecraftDaily does. The problem with my current setup is...The cartography part will take longer and longer the more the game is played (it has to make a bigger more complex map). When I first ran the script it took 5 mins. Now it takes over an hour and a half.

Which is why I wrote minecraftDaily. So that once the maps are made. It does the logs part, then make thumbnails (after the maps are done), and after all that restart the game server.

The problem with using cron. Is I have to make a guess how long cartography will take to make the create thumbnails and restart run at the right time...

---

### Post by CharlesA on 2010-10-12
Yeah, what a pain in the butt.

I don't know if it's Cron having a problem with running those commands, since they have spaces in them or not. It's rather confusing. =/

The strange part is that the commands "should" be run one after the other, but it seems like they aren't. I know when I run my backup script, it does everything in sequential order without running everything at once.

I kinda think that maybe it's due to the way the minecraft script is setup, but I have no idea where to start.

EDIT: Just saw yer edit for a couple posts up. If it dumps out the "Failed" message, it means that the minecraft.sh script exited with a status that wasn't 0 (or successfully completed).

Maybe that's a place to start? Idk.

But anyway, the way you had to set up is that if one script failed to complete, it would move on to the next one, so maybe that's why it seemed like they were all running at the same time?

EDIT2: I've made that mistake as well, so most of my scripts usually look like the line in post 13, that means that if the first command doesn't complete successfully, it exits the script, instead of running everything else that is listed.

Try running minecraft.sh like so:

```
{ /usr/bin/minecraft.sh backup clean; } 1> /home/user/debug.log 2> /home/user/error.log
```

That'll output stdout to /home/user/debug.log and any error messages to /home/user/error.log

---

### Post by Barriehie on 2010-10-12
> **CharlesA said:**
> Sorta. The method you've got working now would probably be better.

I was thinking of just creating 4 seperate scripts that would be run by one master script.

+1

I've done this before to stage process' until priors are completed.
```

mm hh * * * user command && sleep 0; command && sleep 0; etc. etc. etc.
```

---

### Post by HighCommander540 on 2010-10-12
> **CharlesA said:**
> Yeah, what a pain in the butt.

I don't know if it's Cron having a problem with running those commands, since they have spaces in them or not. It's rather confusing. =/

The strange part is that the commands "should" be run one after the other, but it seems like they aren't. I know when I run my backup script, it does everything in sequential order without running everything at once.

I kinda think that maybe it's due to the way the minecraft script is setup, but I have no idea where to start.

EDIT: Just saw yer edit for a couple posts up. If it dumps out the "Failed" message, it means that the minecraft.sh script exited with a status that wasn't 0 (or successfully completed).

Maybe that's a place to start? Idk.

But anyway, the way you had to set up is that if one script failed to complete, it would move on to the next one, so maybe that's why it seemed like they were all running at the same time?

EDIT2: I've made that mistake as well, so most of my scripts usually look like the line in post 13, that means that if the first command doesn't complete successfully, it exits the script, instead of running everything else that is listed.

Try running minecraft.sh like so:

```
{ /usr/bin/minecraft.sh backup clean; } 1> /home/user/debug.log 2> /home/user/error.log
```

That'll output stdout to /home/user/debug.log and any error messages to /home/user/error.log

For the first part. IDK, because like I said I don't get any errors if the are separate lines in the cron. And I never get any errors if I run them manually. That was the first thing I checked (returning 0 or not).

The reason why I can tell that they all run at once, is because I have them output something to scree. And each command outputs something different. And they all seem to run at once output their stuff (just a few of the lines though). When I use "&&" only the first one runs (obviously).

Anyway...I am going to try what Barriehie said. And let yo guys know.

---

### Post by HighCommander540 on 2010-10-12
[SIZE="5"][COLOR="Red"]**I found the solution!!!!!**[/COLOR][/SIZE]

My apologies for the double post, but I figured it out so I thought I would tell you guys the good news.

Anyway I did it by splicing together a few things the people in this topic have suggested. And yes it was the spaces issue.

I didn't know that the `<command>` could be used to store output of a command into a variable. And at first I thought they were apostrophes. So thinking about that I changed my minecraftDaily script to this:

```
`/usr/bin/minecraft.sh backup clean`
`/usr/bin/minecraft.sh cartography`
`/usr/bin/minecraft.sh logs clean`
`/usr/bin/minecraft.sh restart warn`

```

And now it works 100 perfectly. Thanks for helping me out. I never would have got it if you hadn't mentioned the thing about spaces!

---

