---
title: "How would I write a bash script to check for duplicate entries in a HOSTS file?"
date: 2009-12-07
forum: New to Ubuntu
---

### Post by k3lt01 on 2009-12-07
I am playing around with my HOSTS file so that when my server is fully functioning I can put it on the server and let the server do the work leaving my laptop and desktop computers to be as basic as possible.

What I have done is added a couple of freely available HOSTS files together and put them on the end of the standard Ubuntu HOSTS file. In the interests of a clean file I would like to check it easily for duplicate entries whenever I add more to it. Is there a way to write a bash script that will do this for me? or is this something beyond the capabilities of a bash script?

---

### Post by falconindy on 2009-12-07
You can blindly do a once over on the file to make sure that no IPs are repeated.

```
sudo cp /etc/hosts{,.backup}
cat /etc/hosts.backup | grep ^# | sort -u | sudo tee /etc/hosts
```

---

### Post by k3lt01 on 2009-12-07
> **falconindy said:**
> You can blindly do a once over on the file to make sure that no IPs are repeated.

```
sudo cp /etc/hosts{,.backup}
cat /etc/hosts.backup | grep ^# | sort -u | sudo tee /etc/hosts
``` Thanks for that. I just tried it and because the file is so large it listed it in the terminal but as it kept listing the lower alphabetical order was not viewable anymore. It seems the terminal wont keep it all available for viewing. I should have known that would happen ;)

Many are repeated, just as I though, but there are still quite a few single entries.

Any other ideas? all help is greatly appreciated.

EDIT: Just went and checked the HOSTS file itself, because my browser started acting strange. This action totally re-wrote the original file, including the section at the beginning which Linux needs to be at the beginning.

---

### Post by falconindy on 2009-12-08
> **k3lt01 said:**
> Thanks for that. I just tried it and because the file is so large it listed it in the terminal but as it kept listing the lower alphabetical order was not viewable anymore. It seems the terminal wont keep it all available for viewing. I should have known that would happen ;)

Many are repeated, just as I though, but there are still quite a few single entries.

Any other ideas? all help is greatly appreciated.

EDIT: Just went and checked the HOSTS file itself, because my browser started acting strange. This action totally re-wrote the original file, including the section at the beginning which Linux needs to be at the beginning.
1) The file was listed in the terminal because that's a side effect of the 'tee' command -- output is still sent to stdout but it's T'ed off to a file as well.

2) If you weren't getting the results you expected, its because your duplicate entries are only duplicates on a semantic level. There must be differences (likely white space) between the "duplicate" lines of data. The file likely requires a pass with sed to unify the lines.

3) Comments are comments. It is **extremely** rare that any OS program reads them. The hosts file is no special case. Likely, something was changed (incorrectly) when it was parsed. This is why you have a backup ;)

---

### Post by k3lt01 on 2009-12-08
> **falconindy said:**
> The file likely requires a pass with sed to unify the lines. Can you explain this a little bit more please?

---

### Post by falconindy on 2009-12-08
> **k3lt01 said:**
> Can you explain this a little bit more please?
Consider the following two lines:
```
1.2.3.4 hostname.domain
1.2.3.4                           hostname.domain
```
As far as you and I are concerned, these lines are equivalent. They convey the same information. As far as a program such as 'sort' is concerned, they're completely different. That may be the cause of some duplicates still in the file. Also, I realized there's another way (easier for me) to "unify" this structure:

```
cat /etc/hosts | grep -v # | awk '{for (i=1;i<=NF;i++) printf "%s ", $i; print ""}' | sort -u > ~/hosts
```

This will print each field separated by a single space. Unless there's other anomalies that you haven't mentioned, this should clean things up a bit.

---

### Post by bodhi.zazen on 2009-12-08
How about a one-liner ?

```
#!/bin/bash

#backup
cp -i /etc/hosts /root/hosts.bak

cat /etc/hosts | sort | uniq >| /etc/hosts
```

For details, see man uniq

The sort is helpful to sort the chaos of hundreds or thousands of hosts, but is not necessary.

---

### Post by falconindy on 2009-12-08
> **bodhi.zazen said:**
> How about a one-liner ?

```
#!/bin/bash

#backup
cp -i /etc/hosts /root/hosts.bak

cat /etc/hosts | sort | uniq >| /etc/hosts
```

For details, see man uniq

The sort is helpful to sort the chaos of hundreds or thousands of hosts, but is not necessary.
Except that 'uniq' and 'sort -u' behave very similarly. Neither one will account for differences in whitespace.

---

### Post by k3lt01 on 2009-12-08
I understand what you mean so far the bit below didn't seem to work though

> **falconindy said:**
> Also, I realized there's another way (easier for me) to "unify" this structure:

```
cat /etc/hosts | grep -v # | awk '{for (i=1;i<=NF;i++) printf "%s ", $i; print ""}' | sort -u > ~/hosts
```

This will print each field separated by a single space. Unless there's other anomalies that you haven't mentioned, this should clean things up a bit.

```
michael@michael-laptop:~$ cat /etc/hosts | grep -v # | awk '{for (i=1;i<=NF;i++) printf "%s ", $i; print ""}' | sort -u > ~/hosts
Usage: grep [OPTION]... PATTERN [FILE]...
Try `grep --help' for more information.
michael@michael-laptop:~$ 
```

---

### Post by k3lt01 on 2009-12-08
> **bodhi.zazen said:**
> How about a one-liner ?

```
#!/bin/bash

#backup
cp -i /etc/hosts /root/hosts.bak

cat /etc/hosts | sort | uniq >| /etc/hosts
```

For details, see man uniq

The sort is helpful to sort the chaos of hundreds or thousands of hosts, but is not necessary.copy and pasting this as one copy/paste action into terminal just produces this

```
michael@michael-laptop:~$ #!/bin/bash
michael@michael-laptop:~$ 
michael@michael-laptop:~$ #backup
michael@michael-laptop:~$ cp -i /etc/hosts /root/hosts.bak
cp: accessing `/root/hosts.bak': Permission denied
michael@michael-laptop:~$ 
michael@michael-laptop:~$ cat /etc/hosts | sort | uniq >| /etc/hosts
bash: /etc/hosts: Permission denied
michael@michael-laptop:~$ 
```Scripting is something I haven't got a clue about so please treat me like a student and give me an explanation.

I will check the man page to.

---

### Post by falconindy on 2009-12-08
Oh. My bad. Change grep's options to:

-v "^#"

-v means ignore lines with the pattern given. The pattern given matches lines starting with a #.

---

### Post by k3lt01 on 2009-12-08
> **falconindy said:**
> Oh. My bad. Change grep's options to:

-v "^#"

-v means ignore lines with the pattern given. The pattern given matches lines starting with a #.

So it should now read like
```
cat /etc/hosts | grep -v "^#" | awk '{for (i=1;i<=NF;i++) printf "%s ", $i; print ""}' | sort -u > ~/hosts
```

Edit: That worked a treat thanks, there are just under 20000 lines in my HOSTS file, now I need to somehow easily delete duplicates without having to manually read each line.

---

### Post by bodhi.zazen on 2009-12-08
You will have to run the script as root

sudo ./script

to remove white space, I suggest tr

```
# This command will both make a backup and remove white space and remove dups
sudo bash -c "sort /etc/hosts | tr '\t'  ' ' | tr -s ' ' | uniq > /root/hosts.bak"
```If you are happy with the looks of /root/hosts.bak

```
sudo cp /root/hosts.bak /etc/hosts
```Script :

```
#!/bin/bash
sort /etc/hosts | tr '\t'  ' ' | tr -s ' ' | uniq >| /root/hosts.new
mv /root/hosts.new /etc/hosts
```

---

### Post by slakkie on 2009-12-08
```

hosts=$(sed -r 's#\s+# #g' /etc/hosts | grep -v "^#" | sort -u)
echo -e "$hosts" | sudo tee /etc/hosts

```

---

### Post by k3lt01 on 2009-12-08
> **bodhi.zazen said:**
> You will have to run the script as root

sudo ./script

to remove white space, I suggest tr

```
# This command will both make a backup and remove white space and remove dups
sudo bash -c "sort /etc/hosts | tr '\t'  ' ' | tr -s ' ' | uniq > /root/hosts.bak"
```If you are happy with the looks of /root/hosts.bak The resulting file is empty for some reason.

---

### Post by bodhi.zazen on 2009-12-08
Not empty here, even with a direct cut and paste

Note: /etc/hosts is simplified here, just a mix of tabs and spaces + localhost

formatting was lost , so I added tabs and spaces

> sudo cat /etc/hosts

127.0.0.1 <tab> localhost
127.0.0.1 <tab>localhost
127.0.0.1        <sp><sp>localhost
127.0.0.1        <sp>localhost

sudo rm /root/hosts.bak

sudo cat /root/hosts.bak
cat: /root/hosts.bak: No such file or directory

sudo bash -c "sort /etc/hosts | tr '\t'  ' ' | tr -s ' ' | uniq > /root/hosts.bak"

[COLOR=darkgreen] sudo cat /root/hosts.bak

127.0.0.1 localhost[/COLOR]

---

### Post by k3lt01 on 2009-12-08
Thanks for your patience, like I said scripting is something I haven't got a clue about, I have no doubt I have missed something along the way here.

Would you step by step that process for me, I think its the only way I'll get it working correctly and learn from the process. Sorry to be a pain in the proverbial.

---

### Post by k3lt01 on 2009-12-08
> **slakkie said:**
> ```

hosts=$(sed -r 's#\s+# #g' /etc/hosts | grep -v "^#" | sort -u)
echo -e "$hosts" | sudo tee /etc/hosts

```Thanks for this slakkie, I haven't tried it yet as I want to be able to check it before it is copied back into /etc/hosts. Does this remove any duplicates? from the other scripts posted it looks like there are about 3000 duplicate lines between the two HOSTS I have merged.

---

### Post by bodhi.zazen on 2009-12-08
OK

First scripting is nothing more then bash commands in a text file with #!/bin/bash at the top.

You then make the script executable with chmod

chmod a+x ./script

and run it 

./script

You can add it to your path by putting it in ~/bin

The command I (and others) gave you nothing more then a series of commands linked together with a pipe, or |

so the output of command 1 is sent to command 2 ;)

the rest is in man 
man grep
man awk
man unique
mand sort
man tr

combined with an understanding of regular expressions and what escape sequences are in the bash shell ( \t is a tab , \n is a new line, etc).

 So, the command I gave you 

1. sort /etc/hosts -> pipe the output to 
2. tr '\t'  ' ' -> replace tabs with a single space, note syntax '\t'<sp>'<sp>'
3. tr tr -s ' ' -> compress all spaces to a single space
 * see man tr for details
4. uniq -> now that we have removed all white space, list all names once.

5. > /root/hosts.bak = redirect output to /root/hosts.bak

If you wish to learn bash scripting, you really need to start with learning to read man pages . They are hard at first, but they tell you all you need to know and serve as a reference.

Then look at this site : [http://linuxcommand.org/](http://linuxcommand.org/)

Regular expressions are another issue, see

[http://www.zytrax.com/tech/web/regex.htm](http://www.zytrax.com/tech/web/regex.htm)

Again, no one memorized regular expressions, we learn them with use and know where to look for examples (google is your friend).

---

### Post by k3lt01 on 2009-12-08
> **bodhi.zazen said:**
> OK

First scripting is nothing more then bash commands in a text file with #!/bin/bash at the top.

You then make the script executable with chmod

chmod a+x ./script

and run it 

./script

You can add it to your path by putting it in ~/bin

The command I (and others) gave you nothing more then a series of commands linked together with a pipe, or |

so the output of command 1 is sent to command 2 ;)

the rest is in man 
man grep
man awk
man unique
mand sort
man tr

combined with an understanding of regular expressions and what escape sequences are in the bash shell ( \t is a tab , \n is a new line, etc).

 So, the command I gave you 

1. sort /etc/hosts -> pipe the output to 
2. tr '\t'  ' ' -> replace tabs with a single space, note syntax '\t'<sp>'<sp>'
3. tr tr -s ' ' -> compress all spaces to a single space
 * see man tr for details
4. uniq -> now that we have removed all white space, list all names once.

5. > /root/hosts.bak = redirect output to /root/hosts.bak

If you wish to learn bash scripting, you really need to start with learning to read man pages . They are hard at first, but they tell you all you need to know and serve as a reference.

Then look at this site : [http://linuxcommand.org/](http://linuxcommand.org/)

Regular expressions are another issue, see

[http://www.zytrax.com/tech/web/regex.htm](http://www.zytrax.com/tech/web/regex.htm)

Again, no one memorized regular expressions, we learn them with use and know where to look for examples (google is your friend).

Thanks Bodhi,zazen. I'll take a look at the links you supplied. I have read through the man pages even before this thread, you're right they are not the easiest to get a grip on.

---

### Post by bodhi.zazen on 2009-12-09
Aye, the man pages are intimidating, but once you get the hang of it you will be glad you did.

Just keep on asking for assistance, asking questions, trying new things, and read.

---

### Post by slakkie on 2009-12-09
> **k3lt01 said:**
> Thanks for this slakkie, I haven't tried it yet as I want to be able to check it before it is copied back into /etc/hosts. Does this remove any duplicates? from the other scripts posted it looks like there are about 3000 duplicate lines between the two HOSTS I have merged.

If you want to see the output before you write to the /etc/host file just do:

```

hosts=$(sed -r 's#\s+# #g' /etc/hosts | grep -v "^#" | sort -u)
echo -e "$hosts"

```
I've captured the output of in a variable which I then echo to the hostfile, if you remove the | sudo tee /etc/hosts from the original code I gave you it will send output to your terminal.

---

### Post by k3lt01 on 2009-12-09
@bodhi.zazen - I'm working on it, lol.

@slakkie - Thanks mate, much appreciated.

@falconindy - Thanks for your help, I have gone more in your direction and it is working well now.

@ the 3 of you - I'll work on each one as they are all a bit different, even though they will have the same outcome in the long run. Its just a matter of me getting used to this. cli seems to be the heart of Linux and I really do want to figure out what methods I will be most comfortable with.

---

### Post by slakkie on 2009-12-10
> **k3lt01 said:**
> @bodhi.zazen - I'm working on it, lol.

@slakkie - Thanks mate, much appreciated.

@falconindy - Thanks for your help, I have gone more in your direction and it is working well now.

@ the 3 of you - I'll work on each one as they are all a bit different, even though they will have the same outcome in the long run. Its just a matter of me getting used to this. cli seems to be the heart of Linux and I really do want to figure out what methods I will be most comfortable with.

It is like Perl's motto, there is more than one way to do it.

---

