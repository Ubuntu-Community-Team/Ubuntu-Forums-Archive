---
title: "How to tell whether online or offline in a script?"
date: 2010-06-18
forum: New to Ubuntu
---

### Post by Paddy Landau on 2010-06-18
In a script, how can I tell whether the machine is online or offline, i.e. whether it is connected to the Internet?

---

### Post by inversecow on 2010-06-18
> **Paddy Landau said:**
> In a script, how can I tell whether the machine is online or offline, i.e. whether it is connected to the Internet?

Here's a quick little diddy if shellscript is your taste:
```

ONLINE=$( /bin/ping -c1 google.ca | grep '0 received' ); \
if [ -z "$ONLINE" ]; \
  then \
    printf "Your ONLINE\n"; \
  else \
    printf "Your OFFLINE\n"; \
fi;

```

---

### Post by Paddy Landau on 2010-06-18
Ah, so you use [FONT=Courier New]ping[/FONT] to find out.

Looking at the manual, the -W option would be suitable:
```
ping -W1 -q -c1 google.ca
```I'll mark this as solved, thank you.

---

### Post by Paddy Landau on 2010-06-18
It's a bit more complicated, because ping returns status 1 and no stdout when it can't connect. So, the script needs to check for '1 received' rather than '0 received'.

---

### Post by inversecow on 2010-06-21
> **Paddy Landau said:**
> It's a bit more complicated, because ping returns status 1 and no stdout when it can't connect. So, the script needs to check for '1 received' rather than '0 received'.

Hm...
Have you considered `fping`?

# INSTALL
```
sudo apt-get install fping -y
```

# OUTPUT (if pingable)
```
fping -a $HOSTNAME
```

# OUTPUT (if unpingable)
```
fping -u $HOSTNAME
```

---

### Post by Paddy Landau on 2010-06-22
> **inversecow said:**
> Have you considered `fping`?
Perfect! Thank you.

---

### Post by karthick87 on 2010-06-22
> **inversecow said:**
> Here's a quick little diddy if shellscript is your taste:
```

ONLINE=$( /bin/ping -c1 google.ca | grep '0 received' ); \
if [ -z "$ONLINE" ]; \
  then \
    printf "Your ONLINE\n"; \
  else \
    printf "Your OFFLINE\n"; \
fi;

```


How to run this shell script..?

---

### Post by philinux on 2010-06-22
> **getyourkarthick said:**
> How to run this shell script..?

Put it in a text file using say gedit. I use .sh so I can tell what the are.

Right click your file, properties then permissions tab. Tick allow executing file as program. Then double click the file to run it.

I put mine in a folder called scripts. I then use a launcher for it to avoid the normal dialog popping up.

---

### Post by karthick87 on 2010-06-22
> **philinux said:**
> Put it in a text file using say gedit. I use .sh so I can tell what the are.

Right click your file, properties then permissions tab. Tick allow executing file as program. Then double click the file to run it.

I put mine in a folder called scripts. I then use a launcher for it to avoid the normal dialog popping up.

Do you want me have the following line [COLOR=Blue]#!/bin/bash[/COLOR] [COLOR=Black]infront of the file..?[/COLOR]

---

### Post by Paddy Landau on 2010-06-22
> **getyourkarthick said:**
> How to run this shell script..?
I would make it a bit simpler than that now that we have fping to use.

Create a file that contains the following.
```
#!/bin/bash

# Check whether the Internet connection is working.
fping -q google.com    # Choose any arbitrary reliable domain.
if [[ ${?} == 0 ]]
then
    echo 'Your Internet connection is working :)'
else
    echo 'Your Internet connection is not working :('
fi
```Right-click the file in Nautilus and select Properties > Permissions > Allow to execute. Or, in a terminal, use the command:
```
chmod +x myscript
```(Substitute *myscript* for the name of your file.)

Then you can execute your file from the terminal as
```
./myscript
```

---

### Post by philinux on 2010-06-22
> **getyourkarthick said:**
> Do you want me have the following line [COLOR=Blue]#!/bin/bash[/COLOR] [COLOR=Black]infront of the file..?[/COLOR]

It's optional. The # means it's a comment.

---

### Post by karthick87 on 2010-06-22
> **philinux said:**
> It's optional. The # means it's a comment.


Thank you :)

---

### Post by Paddy Landau on 2010-06-22
> **philinux said:**
> It's optional. The # means it's a comment.
That's incorrect if beginning with [FONT=Courier New]#![/FONT] on the first line.

From the bash manual:
> If the program is a file beginning with #!, the remainder of the first line specifies an interpreter for the program. The shell executes the specified interpreter on operating systems that do not handle this executable format themselves. The arguments to the interpreter consist of a single optional argument following the interpreter name on the first line of the program, followed by the name of the program, followed by the command arguments, if any.#!/bin/bash tells the computer that this is a bash script, as opposed to sh or csh or whatever.

I believe that the default on Ubuntu is bash, but by using it explicitly, it makes your script more portable.

---

