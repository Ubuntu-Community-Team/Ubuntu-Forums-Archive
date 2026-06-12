---
title: "Search Text file with GREP for MAC address"
date: 2009-05-21
forum: New to Ubuntu
---

### Post by dafuzzbudd on 2009-05-21
Im using macmanager command that basically puts out "Mac Address is: 00:00:00:00:00:00"
I need to set the MAC as a variable.  I cant figure out grep, this looks possible but I can't find great help with grep.

Please help me!

---

### Post by Celauran on 2009-05-21
Is this what you're looking for?

```
grep -i '[0-9A-F]\{2\}\(:[0-9A-F]\{2\}\)\{5\}' filename
```

---

### Post by dafuzzbudd on 2009-05-21
ill be sure to give that a try when i get home.

can you give me a basic rundown on how the commands work?
-i is ignore?  Then it looks like it finds the 2 character before a : then everything after? 
then i do like macvariable=`grep -i '[0-9A-F]\{2\}\(:[0-9A-F]\{2\}\)\{5\}' filename`

saving grep > variable code
mac=`ifconfig -a eth0 | grep "HWaddr" | cut -d " " -f 11` | tr -s : .
email=`grep 'blah' file.dat | cut -d '/' -f2`

---

### Post by Celauran on 2009-05-21
The -i means case insensitive (man grep)

[0-9A-F] means match any character between 0 and 9 or between A and F
{2} means find it twice
: matches :
then the above repeats.

Essentially, find 2 characters in the range [0-9A-F], then find : + 2 characters in the range [0-9A-F], and repeat this last pattern five times.

Sorry I couldn't put that into words better.

---

### Post by dafuzzbudd on 2009-05-21
it doesnt seem to work
```
#!/bin/bash
macvariable=`grep -i '[0-9A-F]\{2\}\(:[0-9A-F]\{2\}\)\{5\}' test.dump`
echo $macvariable
```
produces whole test.dump contents "Current MAC: 00:c0:ca:23:b1:8b (Alfa, Inc.)"

---

### Post by dafuzzbudd on 2009-05-22
MAC=`/sbin/ifconfig|awk '/HWaddr/ {print $5}'`

this will work but sometimes my MAC sets 
00:40:F6:2C:6B:CC:00:00:00:00:00:00

---

### Post by Celauran on 2009-05-22
> **dafuzzbudd said:**
> it doesnt seem to work
```
#!/bin/bash
macvariable=`grep -i '[0-9A-F]\{2\}\(:[0-9A-F]\{2\}\)\{5\}' test.dump`
echo $macvariable
```
produces whole test.dump contents "Current MAC: 00:c0:ca:23:b1:8b (Alfa, Inc.)"

That's how grep works; it returns the line(s) matching the specified pattern. If you're trying to isolate the MAC address, then awk is the way to go. If it's returning too long a string, just have it return a substring.

```
MAC=`/sbin/ifconfig|awk '/HWaddr/ {print substr($5, 0, 18)}'`
```

---

### Post by hexanol on 2009-05-22
You can isolate the pattern with grep with the -o option.

```
~$ grep -E -o '[[:xdigit:]]{2}(:[[:xdigit:]]{2}){5}' <<< "MAC is 0A:bf:12:35:22:FF"
0A:bf:12:35:22:FF
```

---

### Post by dafuzzbudd on 2009-05-22
this looks like exactly what i need
```

MAC=`/sbin/ifconfig|awk '/HWaddr/ {print substr($5, 0, 18)}'`
```
you guys are awsome

---

### Post by ingobaab on 2012-10-01
You don't need grep for that at all:

```
cat /sys/class/net/eth0/address
```

Please remember that the string "HWAddr" depends on the system language.
The string "HWAddr" is "Hardware Adresse" in german i.e.

Hope this helps anyone.

---

