---
title: "Quick question about gzip"
date: 2011-05-18
forum: New to Ubuntu
---

### Post by ClientAlive on 2011-05-18
Hi,

I (think) I just gzipped a directory that I wanted to compress but I'm a little confused about the results.

I expected to see ".gz" at the end of the directory name once it was all said and done. I don't and I need to determine if the directory is actually ".gz" (compressed) or not.

Here's the steps I followed and the results I see:

```

uname@host:/media/Lacie$ la
.Trash-1000  **Ubuntu_10.04_Backup_2011-05-18-img**

```

To see the contents of the disk. It shows what I expected to see. Notice that I've bolded the directory name in question.

Next I ran:

```

sudo -s

```

Then:

```

root@host:/media/Lacie# gzip -r Ubuntu_10.04_Backup_2011-05-18-img

```

Then the cursor moved to the next line down but was all the way to the left of the screen (not at the end of the uname@host... As usual).

It just sat that way for a very long time (maybe 25 or 30 min (it is almost 20 gig of data in that directory). I forgot to add the "v" option that I might see some feedback on what's going on. Ok, so there things sat; and I let it.

Than I checked on it again a min ago and the "uname@host... " stuff appeared before the cursor on that same line below where I initially entered the command. I assumed this meant it ran it's course and the compression on the directory was accomplished.

Finally I ran:

```

la

```

in order to see what I expected to end with ".gz" indicating a compressed file.

Here's what I actually see:

```

root@host:/media/Lacie# la
.Trash-1000  **Ubuntu_10.04_Backup_2011-05-18-img**

```

The names are identical.

How can I determine if this directory was actually compressed or not; and, if it is, what can I do to add the ".gz" to the end of the name so I can tell in the future just by looking at it?

If anyone can help I would sure appreciate it.

Thanks

---

### Post by ClientAlive on 2011-05-18
I'm such a dumbass . . .

I know how to tell but I can't remember what unit of measure the size is given in when I use:

```

ls -l

```

Is it in Kilobytes?

Thanks
---------------------------------------

I just looked at the directories properties in nautilus and it claims it is 19.9 gig. That's the same size it was to begin with. What am I doing wrong here? And why would the terminal act like that and make me think it was doing it's job on the thing?

I don't get it.

---

### Post by ClientAlive on 2011-05-18
I'm sorry for so many posts in a row here but there's something odd going on that I can't figure out.

A min ago when I tried to close the terminal window it told me there was still a process running. The first thing I thought was maybe gzip was still running. So I gace it a couple min and was able to close it fine after that.

Now here's the odd thing.

1) The original directory was 19.9 gig.
2) When I do a "ls -l" I get a figure of 4096 (whatever the unit is)
3) When I look at the directories properties in nautilus it tells me the size is 19.9 gig.
4) The file names of the directory are identical before and after running the gzip command.
5) The contants of the directory viewed in both nautilus and on the command lines contain names that _all_ end in ".gz"

I'm perplexed. I'll wait for someone to come along and explain if they would be so kind. How does something get compressed and not become reduced in size at all? Or is nautilus not giving the correct size?

---

