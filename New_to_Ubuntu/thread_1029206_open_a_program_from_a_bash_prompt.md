---
title: "open a program from a bash prompt"
date: 2009-01-03
forum: New to Ubuntu
---

### Post by B34ST1Y on 2009-01-03
How do I open a program (rather, invoke it) from a bash prompt....by opening a new prompt and running it there?



Another words, I am trying to write a script in perl to call upon "aircrack-ng" with the options "-c $channel -w $capture $interface"  


....


digressing... does anyone know how to (from a bash prompt) open a program in a new bash console?

---

### Post by ken22 on 2009-01-03
Firstly make sure the script is executable.

```
chmod u+x name_of_script
```

Place it in a folder call bin in your home directory.

I think a simple way to do this is to use bash script like:

```
#! /bin/bash
aircrack-ng -c $1 -w $2 $3
```

if you name this script crack, then 

```
crack
``` followed by the three arguments will do it.


This may help with the new shell window thing, though I haven't done it myself.

[http://www.astro.virginia.edu/class/oconnell/astr511/idl_5.1_html/idl1a9.htm]("http://www.astro.virginia.edu/class/oconnell/astr511/idl_5.1_html/idl1a9.htm")

---

### Post by B34ST1Y on 2009-01-03
hmm...that link you provided didn't line up with any relative information to my issue, but I appreciate the effort.

that actually isn't what i'm trying to do. I want the script (deep inside of the script) to call on aircrack-ng with those arguments, but when I try 

<code>
system("airodump-ng -c $channel -w $capture $interface");
</code>

it returns, saying that no interface option specified. (obviously it's just not inputting the command correctly as I verified that the variables were set correctly, and if I type in the variables manually it works fine)

---

### Post by ken22 on 2009-01-03
ok, I have a theory.

When ```
-w $capture $interface
``` is evaluated it doesn't put a space between $capture and $interface and just sticks them together as one string.

Try ```
-w $capture ." ". $interface
```

---

### Post by B34ST1Y on 2009-01-03
ahhh, I think I figured it out. after it specifies the $channel variable, it goes onto a new line for some reason....


....which leaves me bewildered as to why its doing that....... uhh...... :confused:

---

### Post by ken22 on 2009-01-03
perhaps when it is read in, it retains the newline character. chomp it off before using the variable.

---

### Post by B34ST1Y on 2009-01-03
that was it! I needed to chop it! gah! brilliant, thank you so much! :D

---

### Post by ken22 on 2009-01-03
no problem :)

---

