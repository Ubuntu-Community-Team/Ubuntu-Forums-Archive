---
title: "Location of process priorities config file"
date: 2011-04-12
forum: New to Ubuntu
---

### Post by red03golf on 2011-04-12
Hi;
Another newb who has messed with his system ... hehe.

I was experimenting with priorities and changed the update-notifier priority to high.

Now, computer literally takes forever to even restart - 10 mins before mouse would move, 30 mins just to show desktop background.

I booted from Ubuntu on a thumbdrive to get back online and have access again to my file system on my hard drive.

Where can I find the file that has the configuration settings for process priorities so that I can change the update-notifier back to it's default value?

I have done a search for text within files using the term "update-notifier" (to start with) and am going through them slowly to see if I can find it. Also am googling to try to see if there's an existing post somewhere on which file is used to store the processes' priority values.

Thanks for your assistance.

---

### Post by red03golf on 2011-04-13
I've been slowly going through files that mention the update-notifier but I have yet to locate which one contols the priority level.
There's so many #includes in the files - yikes!!
any assistance would be much appreciated in tracking down the file which maintains the priority levels for each process.
Thanks.

---

### Post by grvsaxena419 on 2011-04-13
> **red03golf said:**
> I've been slowly going through files that mention the update-notifier but I have yet to locate which one contols the priority level.
There's so many #includes in the files - yikes!!
any assistance would be much appreciated in tracking down the file which maintains the priority levels for each process.
Thanks.

Can you boot to the system using GUI ? If you can try using command 
> nice -n 10 update-notifier 

If you cant boot to GUI try pressing alt+ctrl+f1 and then login to command line and try this command

---

### Post by red03golf on 2011-04-13
GUI takes a very very long time - hours.
I'll try the command line boot and see how that goes.
Thanks for the post.

---

### Post by red03golf on 2011-04-13
Was able to boot to command line np.
Tried the 'nice' command - unfortunately no luck.
Got this return:
"failed to init the UI: cannot open display"
Tried same command with sudo - same result.

I get the feeling that the process may have to be running at the time and it may not be running under the command line interface. I don't know where to find it to intialize it from the command line and it probably has dependencies anyway that need to be running for it to run.

Perhaps one day there will be some undo tools / options for Ubuntu to return to a previous state or undo updates or revert to previous drivers so that one can have an easy fix for bad updates and silly mistakes.
I know, someone can make an addon / tool / program called " UndUbuntu ".

Luckily I can boot from USB drive, I have access to my hard drive, I have a 2TB external to copy to and I have the USB installation to use to re-install Ubuntu - so I'm ok ... just a few hours re-installing, updating and re-configuring - no big deal really.

I'm quite enjoying this actually. It's my first Linux system and I'm learning new info here and there - am having lots of fun using the terminal and learning to become comfortable with command line over GUI.
Thanks for the assistance.

---

