---
title: "bash: problem with space"
date: 2009-04-26
forum: New to Ubuntu
---

### Post by PGScooter on 2009-04-26
Hi,

The following code does not work. However, when I put the full path in, that is, uncommenting the last line, it works. How can I use the variables?

Thanks

```

directory='/media/storage/My\ Music'
artist='Enya'
ls $directory/$artist/
#ls /media/storage/My\ Music/$artist/

```

---

### Post by |{urse on 2009-04-26
put a / before $directory ?

---

### Post by PGScooter on 2009-04-26
l{urse,

Thank you for the suggestion. It did not fix anything. The variable $directory already has a slash at the start of it. When I do [code]echo "$directory/$artist" it looks exactly like the ls command spelled out, so I am confused.

Any other ideas?

---

### Post by Nepherte on 2009-04-26
Use this:
```
IFS="
"
directory='/media/storage/My Music'
artist='Enya'
ls $directory/$artist/
```
That way you can use spaces in variable assignments like directory and you don't need to use the \ escape character.

---

### Post by bodhi.zazen on 2009-04-26
what error message are you getting ?

---

### Post by spillin_dylan on 2009-04-26
Are you absolutely sure that you need the backslash to escape the space in the $directory string?  Try removing this, and if that doesn't work, put the string in "double quotes" instead.  

I forget which way it is, either 'single quotes' or "double quotes" will ignore special characters (i.e. treat them as any other character), and the other uses them for their special function.  

Another thing to try would be to put your arguement to ls in quotes:
```

directory='/media/storage/My\ Music'
artist='Enya'
ls "$directory/$artist/"
#ls /media/storage/My\ Music/$artist/

```

---

### Post by PGScooter on 2009-04-26
When running the script that I posted, I get the following error message:
```

ls: cannot access /media/storage/My\: No such file or directory
ls: cannot access Music/Enya/: No such file or directory

```

Nepherte,

that works great! thank you for the suggestions-- IFS seems like a nice thing to become familiar with.

spillin,

thanks. Removing the \ did the trick. I think the double quotes worked as well.

---

