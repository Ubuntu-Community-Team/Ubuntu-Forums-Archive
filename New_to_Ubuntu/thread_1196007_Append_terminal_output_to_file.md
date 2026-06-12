---
title: "Append terminal output to file"
date: 2009-06-24
forum: New to Ubuntu
---

### Post by mortuk on 2009-06-24
Hi all

I know you can use ' > /path/to/log/file' at the end of a command to append the output to a log file.

If you run it again it will erase the previous logs. Is there any way to append it to the file so you have a running log of all commands entered?

Reason being I am using this in a crontab command.

---

### Post by drs305 on 2009-06-24
> **mortuk said:**
> Hi all

I know you can use ' > /path/to/log/file' at the end of a command to append the output to a log file.

If you run it again it will erase the previous logs. Is there any way to append it to the file so you have a running log of all commands entered?

Reason being I am using this in a crontab command.

Use ">>" to add the output to the end of the file.

---

### Post by decoherence on 2009-06-24
> **mortuk said:**
> Hi all

I know you can use ' > /path/to/log/file' at the end of a command to append the output to a log file.

If you run it again it will erase the previous logs. Is there any way to append it to the file so you have a running log of all commands entered?

Reason being I am using this in a crontab command.

Use '>> /path/to/log/file'

'>>' means 'append to end of file'

---

### Post by mortuk on 2009-06-24
nice one, cheers :)

---

### Post by Polaris96 on 2009-06-24
just a quick note:  you can put some extra sanity in your logfile by parsing it with an:

echo blahblahblahblah >> OUTFILE

it makes it easier to see where you're at when you review the file

---

### Post by sisco311 on 2009-06-24
or
```
command | tee -a /path/to/file
```
it's useful when you need root privileges in order to write to the file:
```
echo "deb http://my.repo.com bla bla" | sudo tee /etc/apt/sources.list.d/my.repo.list
echo "deb http://my.repo.com bla bla" | sudo tee -a /etc/apt/sources.list.d/my.repo.list
```

---

### Post by decoherence on 2009-06-24
piping to tee for teh win!

---

