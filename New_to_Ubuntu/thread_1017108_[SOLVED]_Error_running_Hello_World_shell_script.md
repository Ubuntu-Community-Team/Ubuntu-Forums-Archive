---
title: "[SOLVED] Error running Hello World shell script"
date: 2008-12-20
forum: New to Ubuntu
---

### Post by ebroyles on 2008-12-20
Hello.

Having trouble running simple bash script.  Getting this error:

bash: testbash.sh: command not found

text of script is as follows:

```
#!/bin/bash
STR='Hello World!'
echo $STR
```

Web search told me that perhaps that error meant that I wasn't referencing bash correctly so I ran ```
$ whereis bash
``` and got the following:

```
bash: /bin/bash /etc/bash.bashrc /usr/share/bash /usr/share/man/man1/bash.1.gz
```

Looks like I am pointing it in the right place

I also made sure that I have execute permissions on the script.

```
-rwxr--r-- 1 edward edward 41 2008-12-20 14:57 testbash.sh

```

Any ideas?  I can run this just fine in the terminal if I type those commands in, but not in a script.  I also tried running it without putting the string into a variable, same error.

Any ideas?

Thanks!

---

### Post by Carl Hamlin on 2008-12-20
-----BEGIN PGP SIGNED MESSAGE-----
Hash: RIPEMD160

- From the directory containing the script, type

./testbash.sh


Even if you're *in* the directory containing the script, you'll have to specify the exact path.

-----BEGIN PGP SIGNATURE-----
Version: GnuPG v1.4.9 (GNU/Linux)

iEYEAREDAAYFAklNfaUACgkQyLm4ydrABvedgACg5IWjuBAVAxY9Rw6lTKtElW+z
zEkAoID8JxWuHEXCqw965NoBIHzqASB0
=cjtH
-----END PGP SIGNATURE-----

---

### Post by sisco311 on 2008-12-20
if your scripts directory is not in the $PATH variable
you must to enter the full path to the script:
```
/path/to/script/testbash.sh
```
or if you are in the scripts directory, then you can use ./ (current working directory):
```
./testbash.sh
```

---

### Post by ebroyles on 2008-12-20
Thanks, guys!

I knew it was something simple.

---

### Post by sisco311 on 2008-12-20
EDIT: never mind

[s]Cool!

Please mark the thread solved by selecting 
**Mark this thread as solved** from the [COLOR="Red"]**Thread Tools**[/COLOR].

Marking threads as [SOLVED], after a solution has been found will help others to find an expedient solution for their own issues.[/s]

---

