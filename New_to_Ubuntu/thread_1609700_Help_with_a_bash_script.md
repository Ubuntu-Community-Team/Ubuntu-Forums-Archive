---
title: "Help with a bash script"
date: 2010-10-30
forum: New to Ubuntu
---

### Post by risegeek on 2010-10-30
Hey guys, I am writing a bash script for a game server map backup - I currently have the script providing feedback to a file that I occasionally 'tail' when I am interested in how my daily backups are going - I would very much like it to give me some feedback on disk usage. I am fairly new to Linux so you will have to excuse me if I am going about this incorrectly.

I was planning on using the 'df' command & from here I was going to use 'awk' to filter out everything but the percentage, I have done a little reading but nothing was too specific.

```

sam@server1:~$ df -h | awk '/%/ {print $5}'
Use%
29%

```

I would like to remove the top-line so I am left with just the percentage :) any and all help is very much appreciated!

Love you Ubuntu :P

---

### Post by Hippytaff on 2010-10-30
I'm no guru (see my past posts) but might the grep command better server your purposes?

---

### Post by sisco311 on 2010-10-30
Hmmm, my first thought was:
```
df -h | awk '!/Filesystem/ && /%/ {print $5}'
```
but, that's not the optimal solution in case you plug in another storage device...

Try to match the mount point; assuming it's the root (/) partition:
```
df | awk '{if ($6 == "/") print $5}'
```

---

### Post by risegeek on 2010-10-30
> **sisco311 said:**
> Hmmm, my first thought was:
```
df -h | awk '!/Filesystem/ && /%/ {print $5}'
```
but, that's not the optimal solution in case you plug in another storage device...

Try to match the mount point; assuming it's the root (/) partition:
```
df -h | awk '{if ($6 == "/") print $5}'
```

That works great! cheers dude :)

I was fooling around with grep initially Hippytaff but after a general tinker I could only really select each of the 2 rows, I am a n00b though. Is it possible to complete the same task using grep? :confused:

---

### Post by Hippytaff on 2010-10-30
> 
 Is it possible to complete the same task using grep?
Don't let the beans fool you, I'm a noob too, the beans are me asking silly questions - I'm a bit more familiar with grep, still can't get my head around awk :-)

---

### Post by sisco311 on 2010-10-30
> **risegeek said:**
> That works great! cheers dude :)


You're welcome!

> **risegeek said:**
> 
I was fooling around with grep initially Hippytaff but after a general tinker I could only really select each of the 2 rows, I am a n00b though. Is it possible to complete the same task using grep? :confused:

I guess, you could use a combination of grep and tr or even sed to accomplish the same task, but awk and perl are very powerful...

My suggestion is to learn all of them and always use the right tool for the job. 

Oh, and don't forget to mark this thread as [SOLVED]. Thanks!

---

### Post by DaithiF on 2010-10-30
rather than run df against all mounted filesystems and then filter down output to the one you want, better to run df against just the mount you need -- less work for df to do, and less chance of picking the wrong output line.

```
df -h / | awk 'END { print $5 }'
```

---

### Post by risegeek on 2010-10-30
> **sisco311 said:**
> You're welcome!



I guess, you could use a combination of grep and tr or even sed to accomplish the same task, but awk and perl are very powerful...

My suggestion is to learn all of them and always use the right tool for the job. 

Oh, and don't forget to mark this thread as [SOLVED]. Thanks!

Well it's good to know I went about using the 'right' tool for the job, I've had alot of fun today writing this script :)I'll be sure to read up on all the the aforementioned tools.

Again thanks, to you too Hippytaff ):P 

Marking this as SOLVED now.

Edit: DaithiF, that works great too :) thank you!

---

### Post by sisco311 on 2010-10-30
> **DaithiF said:**
> rather than run df against all mounted filesystems and then filter down output to the one you want, better to run df against just the mount you need -- less work for df to do, and less chance of picking the wrong output line.

```
df -h / | awk 'END { print $5 }'
```

+1

d'oh, how did I miss that? :redface:

---

### Post by Hippytaff on 2010-10-30
> **DaithiF said:**
> rather than run df against all mounted filesystems and then filter down output to the one you want, better to run df against just the mount you need -- less work for df to do, and less chance of picking the wrong output line.

```
df -h / | awk 'END { print $5 }'
```

That script is sweet, I'm going to use it to keep track of my home partition if that ok with you?

---

