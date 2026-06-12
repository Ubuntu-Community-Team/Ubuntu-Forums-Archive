---
title: "Record duration a program/process is running"
date: 2009-06-06
forum: New to Ubuntu
---

### Post by Commander_Bob on 2009-06-06
I need a way to measure how long I am using a program (Eagle CAD) so I know how long it takes me to complete my projects. I need it to save it's count from previous sessions and have a total time used. Basically a stop watch that automatically starts and stops when the program opens/closes.

Is there anything like this out there?

Thanks,
Justin Rajewski

---

### Post by fatality_uk on 2009-06-06
Not an application I know off hand. Need to have a think. Might be possible to create a script that writes a start time and end time to a launcher.

---

### Post by BugBuster on 2009-06-06
You could try launching the application from the terminal prefixing the name with time command

For example if you were to launch brasero:

$time brasero

then when you exit brasero you would get something like this;

$ time brasero

real	0m6.034s
user	0m0.852s
sys	0m0.232s

That, I believe is what you are looking for.Just make sure you don't close the terminal in the meanwhile!!

---

### Post by sdennie on 2009-06-06
You could wrap your program with a script and sum the times.  This is not a solution but, it's an example on how to do it for a single session run.  You could adapt this to store the information somewhere and later use bc or a spreadsheet to sum it:

```

START=$(date +%s)

do_something

STOP=$(date +%s)
RUNTIME=$(expr $STOP - $START)
HOURS=$(expr $RUNTIME / 3600)
REMAINDER=$(expr $RUNTIME % 3600)
MINS=$(expr $REMAINDER / 60)
SECS=$(expr $REMAINDER % 60)

printf "%02d:%02d:%02d\n" "$HOURS" "$MINS" "$SECS\n"

```

---

### Post by Commander_Bob on 2009-06-06
Thanks a lot! I edited your script to append it to a text file and edited the launcher to start the script instead of eagle directly. Here's what I got.

```
START=$(date +%s)
DATE=$(date)

eagle

STOP=$(date +%s)
RUNTIME=$(expr $STOP - $START)
HOURS=$(expr $RUNTIME / 3600)
REMAINDER=$(expr $RUNTIME % 3600)
MINS=$(expr $REMAINDER / 60)
SECS=$(expr $REMAINDER % 60)

echo $DATE: $HOURS:$MINS:$SECS | cat >> ~/Documents/Time/Eagle.txt
```

It outputs something like this.
```
Sat Jun 6 19:02:03 PDT 2009: 0:0:7
Sat Jun 6 19:05:04 PDT 2009: 0:1:26
```

Shell scripting proves very useful once again.

Justin

---

### Post by sdennie on 2009-06-06
I'm glad it worked.  I would however recommend changing your output to something like this:

```

printf "%s %02d:%02d:%02d %d\n" "$(date)" "$HOURS" "$MINS" "$SECS" "$RUNTIME" >> ~/Documents/Time/Eagle.txt

```

I haven't tried that but, the idea is that you get the date, a regularly formatted elapsed time string and finally, seconds elapsed.  If the ultimate goal is to eventually sum the total elapsed time or generally do something interesting with it, having it as a field in your logs that is easily accessible with cut or awk will make post processing the information MUCH easier.

---

### Post by Commander_Bob on 2009-06-06
Thanks, I changed it and it works fine.

---

