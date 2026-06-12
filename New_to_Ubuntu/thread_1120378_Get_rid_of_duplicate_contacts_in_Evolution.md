---
title: "Get rid of duplicate contacts in Evolution?"
date: 2009-04-08
forum: New to Ubuntu
---

### Post by tahitiwibble on 2009-04-08
Hi,

I have 4000+ contacts, I'll bet 3000 duplicates, in Evolution .......... apparently because of syncing with my Palm stuff.

I found [this answer]("http://zzamboni.org/brt/2006/07/09/eliminating-duplicate-contacts-in-evolution-howto/") to my problem. I copied the script into a terminal and got this;

```
dad@dad-desktop:~$ #!/usr/bin/perl -w
dad@dad-desktop:~$ 
dad@dad-desktop:~$ use DB_File;
bash: use: command not found
dad@dad-desktop:~$ 
dad@dad-desktop:~$ $addrdb=$ARGV[0]
bash: =[0]: command not found
dad@dad-desktop:~$     || "$ENV{HOME}/.evolution/addressbook/local/system/addressbook.db";
bash: syntax error near unexpected token `||'
dad@dad-desktop:~$ print "* Examining $addrdb\n";
Warning: unknown mime-type for "* Examining \n" -- using "application/octet-stream"
Error: no such file "* Examining \n"
dad@dad-desktop:~$ 
dad@dad-desktop:~$ tie %h, 'DB_File', $addrdb, O_RDWR, 0777, $DB_HASH
The program 'tie' is currently not installed.  You can install it by typing:
sudo apt-get install texlive-extra-utils
bash: tie: command not found
dad@dad-desktop:~$   or die "Error opening file: $!\n";
bash: !\n": event not found
dad@dad-desktop:~$ 
dad@dad-desktop:~$ # Keep track of names we've seen
dad@dad-desktop:~$ %names=();
bash: syntax error near unexpected token `;'
dad@dad-desktop:~$ 
dad@dad-desktop:~$ for $k (keys %h) {
bash: syntax error near unexpected token `('
dad@dad-desktop:~$     $card=$h{$k};
bash: ={}: command not found
dad@dad-desktop:~$     if ($card =~ /^FN:(.*)$/m) {
bash: syntax error near unexpected token `('
dad@dad-desktop:~$         $name=$1;
bash: =: command not found
dad@dad-desktop:~$         $name=~s/\r//g;
bash: =~s/r//g: No such file or directory
dad@dad-desktop:~$         chomp $name;
bash: chomp: command not found
dad@dad-desktop:~$         if (exists($names{$name})) {
bash: syntax error near unexpected token `$names{$name}'
dad@dad-desktop:~$             print "* Previously found $name, removing\n";
Warning: unknown mime-type for "* Previously found , removing\n" -- using "application/octet-stream"
Error: no such file "* Previously found , removing\n"
dad@dad-desktop:~$             delete $h{$k};
bash: delete: command not found
dad@dad-desktop:~$         }
bash: syntax error near unexpected token `}'
dad@dad-desktop:~$         $names{$name}++;
bash: {}++: command not found
dad@dad-desktop:~$     }
bash: syntax error near unexpected token `}'
dad@dad-desktop:~$ }
bash: syntax error near unexpected token `}'
dad@dad-desktop:~$ 
dad@dad-desktop:~$ print "* Done. Duplicate statistics:\n";
Warning: unknown mime-type for "* Done. Duplicate statistics:\n" -- using "application/octet-stream"
Error: no such file "* Done. Duplicate statistics:\n"
dad@dad-desktop:~$ print join("\n", map { "$_: $names{$_} times" } 
bash: syntax error near unexpected token `('
dad@dad-desktop:~$            sort { $names{$b} <=> $names{$a} } 
bash: =: No such file or directory
dad@dad-desktop:~$            grep { $names{$_} > 1 } keys %names
grep: {}}: No such file or directory
grep: }: No such file or directory
grep: keys: No such file or directory
grep: %names: No such file or directory
dad@dad-desktop:~$           )."\n";
```

Can anybody tell me why it didn't work? It appears to have very successfully eliminated duplicates for some.

Thanks guys.

---

### Post by tahitiwibble on 2009-04-09
Would anyone here today have an idea?

---

### Post by Didius Falco on 2009-04-09
I did a little looking for this last night, but couldn't find anyone else who'd picked up the script and worked on it.

It also appears to be something the folks at Evolution are working on, but haven't implemented as yet.

I did, however, find this in the comments of the site you got the script from:

> There is an easier way! Create a new address book. Name it whatever you want. Take the two known duplicate entries and drag them there. It will give you the duplicate merge dialog. Merge them. Drag them back. Done!

Not the most elegant solution, but it's better than no solution at all.

Sorry I couldn't be more help.

---

### Post by barretr on 2009-04-13
Are you sure you're using Perl to run the script?

```
perl evo_eliminate_duplicate_contacts.pl 
```

You could also try [UnDupe](http://www.stevenscreek.com/palm/download.html) for PalmOS.

---

### Post by mlentink on 2009-04-13
a .pl script is a perl script, that needs to be interpreted by perl. You cannot just drop it in a terminal.  Run it as per the previous post

---

### Post by tahitiwibble on 2009-04-13
**barretr & mlentink**,

I didn't realize that at all. Thanks to both of you very much for getting back to me! Here goes ..... :)

---

