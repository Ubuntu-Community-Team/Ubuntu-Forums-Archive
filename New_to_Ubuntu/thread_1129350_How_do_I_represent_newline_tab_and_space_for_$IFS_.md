---
title: "How do I represent newline tab and space for $IFS in a shell script"
date: 2009-04-18
forum: New to Ubuntu
---

### Post by hovzio on 2009-04-18
I've been writing a series of shell scripts that run on my system at boot time, one for example is basically an endless loop that checks my auth.log for sshd connect and spits out a visual poppup when someone logs in/out/LOGIN_FAIL.. etc.

I have seen many mentions of shell scripts not being the safest method of doing things in a system, "compiled programs are safer". I assume this to be true since they cannot really be manipulated.. Now I've also been reading that by manipulating $IFS its possible to maipulate shell scripts into doing damage.. one should set the IFS at the beggining of a script and declare it read only (unless you need to use it I guess). Sounds cool, how do I make IFS= newline space tab. How do I properly represent these charachters. like "\n or \t" or do I physically hit a newline, tab .. withing a single quote. I have googled this and am not really finding what I'm looking for, lots of info on how I can manipulate IFS for word splitting etc which I am familiar with.I am familiar with shell scripting an basic syntax but never have I decided to set IFS to a standard value within a script. Appreciate any input on the subject, also in terms of IFS and security.. is this really an issue and how can I properly represent newline and co?  Thanks :)

---

### Post by blueridgedog on 2009-04-18
Here is an example:

#!/bin/bash
myvar="test \t and more test"
echo -e $myvar


note the -e to turn on escape chars.

I think shell scripts are just fine to run in the way you describe and have used them for years.  If nothing else, they are a great way to learn.

---

### Post by hovzio on 2009-04-18
> **blueridgedog said:**
> Here is an example:

#!/bin/bash
myvar="test \t and more test"
echo -e $myvar


note the -e to turn on escape chars.

I think shell scripts are just fine to run in the way you describe and have used them for years.  If nothing else, they are a great way to learn.

Hi, sorry this doesn't seem help. (or I missunderstood, ;)  ) What I'm looking to do is set the standard/default IFS variable in a script to readonly. I want to know how to properly assign a tab/newline/space to IFS.I have tried this and similar:

```
IFS=\t\n 

```

EDIT:    This doesn't seem to work, I'm not quite sure yet.I'm probably doing somthing wrong.how do I represent the space charachter?Thanks

---

### Post by blueridgedog on 2009-04-18
This site:

[http://www.dwheeler.com/secure-programs/Secure-Programs-HOWTO/environment-variables.html](http://www.dwheeler.com/secure-programs/Secure-Programs-HOWTO/environment-variables.html)

States the following:

One environment value you'll almost certainly re-add is PATH, the list of directories to search for programs; PATH should not include the current directory and usually be something simple like ``/bin:/usr/bin''. Typically you'll also set IFS (to its default of `` \t\n'', where space is the first character) and TZ (timezone). Linux won't die if you don't supply either IFS or TZ, but some System V based systems have problems if you don't supply a TZ value, and it's rumored that some shells need the IFS value set. In Linux, see environ(5) for a list of common environment variables that you might want to set.

So, the syntax that would work seems like:

IFS=" \t\n"
export $IFS

(after you set an environment variable, you need to export it to have it impact anything other than the current script)

As an aside, be careful...if you break IFS, you break many many things.

---

### Post by hovzio on 2009-04-19
> **blueridgedog said:**
> This site:

[http://www.dwheeler.com/secure-programs/Secure-Programs-HOWTO/environment-variables.html](http://www.dwheeler.com/secure-programs/Secure-Programs-HOWTO/environment-variables.html)

States the following:

One environment value you'll almost certainly re-add is PATH, the list of directories to search for programs; PATH should not include the current directory and usually be something simple like ``/bin:/usr/bin''. Typically you'll also set IFS (to its default of `` \t\n'', where space is the first character) and TZ (timezone). Linux won't die if you don't supply either IFS or TZ, but some System V based systems have problems if you don't supply a TZ value, and it's rumored that some shells need the IFS value set. In Linux, see environ(5) for a list of common environment variables that you might want to set.

So, the syntax that would work seems like:

IFS=" \t\n"
export $IFS

(after you set an environment variable, you need to export it to have it impact anything other than the current script)

As an aside, be careful...if you break IFS, you break many many things.

Very cool, thanks. I will read up on that link many thanks blueridgedog.

EDIT: Very, very cool link, this is exactly what I was looking for..

---

