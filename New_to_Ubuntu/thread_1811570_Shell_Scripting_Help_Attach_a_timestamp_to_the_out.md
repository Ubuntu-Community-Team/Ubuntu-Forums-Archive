---
title: "Shell Scripting Help: Attach a timestamp to the output file."
date: 2011-07-25
forum: New to Ubuntu
---

### Post by eamonn on 2011-07-25
Hello,

I'm trying to work on a, really simple, shell script for a class project. The objectives are to:

1) Run the "date" command.
2) Run the "df -h" command.
3) Run the "ifconfig" command.
4) Create a logfile similar to "goodoutput.072511.txt" where "072511" is the date and can be changed whenver the script is ran again. So that if the script is run on Thursday it will create the logfile "goodoutput.072811.txt"

I'm able to create a script that accomplishes the first three objectives and I'm able to create an output file but I'm not able to attach a timestamp to the output file. I hate fishing for answers but I'm at the point where I don't think asking for help would hurt at all.

This is the script that I've been working with:

> 
#bin/bash
#Linux Configuration Lab 5
date 1>goodoutput
df -h>goodoutput
ifconfig>goodoutput

I've tried looking an answer on Google and the book we're using (Linux+ Guide to Linux Certification by Jason W. Eckert and M. John Schitka) but I haven't had any luck. I'm using 11.04.

---

### Post by ddastoor on 2011-07-25
```
filename="logfile.`date '+%m%d%Y'`.log"
echo $filename
```

gives:
logfile.07252011.log

If you want variations on the format specifiers (%m, etc), see:

[http://linux.die.net/man/3/strftime]("http://linux.die.net/man/3/strftime")

or do a :
```
man strftime
```

---

### Post by ddastoor on 2011-07-25
sorry forgot to mention.... 

this is used a lot in shell scripting:

variabe="plain_text_`<linux command>`_more_plain_text"

where the `` are backquotes (next to the 1 key near the function keys)

---

### Post by sisco311 on 2011-07-25
`COMMANDS` is an older form of command substitution. The usage of the POSIX-form $(COMMANDS) is preferred.

---

### Post by eamonn on 2011-07-25
This worked great. Thank you.

---

### Post by eamonn on 2011-07-25
> **sisco311 said:**
> `COMMANDS` is an older form of command substitution. The usage of the POSIX-form $(COMMANDS) is preferred.

I'm not sure what you mean. Are you saying that there's a more preferred way to write "variable="plain_text_`<linux command>`_more_plain_text"?

---

### Post by nothingspecial on 2011-07-25
> **eamonn said:**
> I'm not sure what you mean. Are you saying that there's a more preferred way to write "variable="plain_text_`<linux command>`_more_plain_text"?

The bit inside the backticks or the $() is command substitution.

backticks is the oldway

$() is now the correct way

```
command > outputfile-$(date +"%m-%d-%y")
```

---

### Post by ddastoor on 2011-07-25
> **sisco311 said:**
> `COMMANDS` is an older form of command substitution. The usage of the POSIX-form $(COMMANDS) is preferred.


Your right, except that the $() format doesn't work in the c shell (csh)

Backquotes `` works atleast in bash/csh/ksh (k shell)

Yes, nowadays, mostly, I'm guessing that all new scripts will use bash (IMO, the best for shell scripting), so $() will work fine ... for e.g.:

```
 variable=$(date) 
```

---

