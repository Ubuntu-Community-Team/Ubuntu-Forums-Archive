---
title: "Teach me about rsync!"
date: 2009-02-22
forum: New to Ubuntu
---

### Post by Kareeser on 2009-02-22
The man pages are woefully complex and confusing... sigh.

Anyways, I've been messing around with backups using rsync, which works great over ssh as well.

```
rsync -avz -e ssh [source] [destination]
```

Except I don't completely understand the behaviour... let's say there's a file "a.txt" on Computer 1. If I run rsync, now both Computer 1 and 2 have "a.txt".

What happens if I rename "a.txt" to "b.txt", and run rsync again? Will both computers have copies of "a.txt" and "b.txt", or is rsync smart enough to realize that a.txt was renamed, and rename "a.txt" as "b.txt" on Computer 1?

Secondly, does it matter which order I put the source and destination computers?

With most terminal commands, I can think of it as "from" and "to", i.e.
```

cp /home/user/secret_nuclear_launch_codes /var/www/
   ^^ from                                ^^ to

```

but is this the same in rsync as well? "Source" and "Destination", as said in the man page, seems to suggest that ONLY the file at the destination will be modified... is this true?

===

Upon experimentation, I've come to realize that renamed files are simply considered different files, and copies will be synchronized over. Not bad. Safe behaviour.

---

### Post by prinny42 on 2009-02-22
Rsync won't, by default get rid of a.txt from the destination if you rename it to b.txt at the source, you will simply end up with a.txt and b.txt at the destination.  However, if you include the --delete option, rsync will delete anything that is at the destination that is not at the source.

You should be very careful with --delete, and it is generally best to do a dry run first with the option -n to make sure that it's going to do what you expect it to.

As far as I know, the syntax is invariably in the same "from/to" form that you describe.

Rsync will indeed only affect the destination by default.  I believe there are options to modify this behavior (though I haven't actually checked), but I've never looked into these.

Also, in case you didn't notice, please note that whether or not you include a final / in the source matters.

The command below would sync ~/blah and all its contents to ~/pera.
```
rsync -av ~/blah ~/pera
```

However, the command below now would sync the contents of ~/blah, but not ~/blah itself, to ~/pera.
```
rsync -av ~/blah/ ~/pera
```

---

### Post by Kareeser on 2009-02-22
Thanks for the heads-up. I always get the trailing slash confused and treat it as though it were not needed.

Thanks!

---

