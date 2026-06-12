---
title: "Unpurged packages."
date: 2010-01-15
forum: New to Ubuntu
---

### Post by da burger on 2010-01-15
Is there a terminal command I can use to get a list of all the packages that have been uninstalled but have not been purged. A list like this is available in synaptic but I need it for a script so it must be a bash command.

---

### Post by Brandon Williams on 2010-01-15
The will print the name of any package in state 'rc' (removed by still configured).

```
dpkg -l | awk '$1 == "rc" { print $2; }'
```

---

### Post by slakkie on 2010-01-15
```

dpkg -l | tail -n +6 | grep -v '^ii' | awk '{print $2}'

```
That is the line you want.

And to purge them all at once:

```

sudo aptitude purge $(dpkg -l | tail -n +6 | grep -v '^ii' | awk '{print $2}')

```

---

### Post by da burger on 2010-01-15
Thanks a lot that is great!
Would you mind breaking that down (I like to know what commands I am running)!

---

### Post by Brandon Williams on 2010-01-15
"dpkg -l" prints a list of all packages that have some recorded installation state. The state will appear in the first column of the output, and it will typically be either 'ii' (installed packages) or 'rc' (removed but still configured). The package name will appear in column 2.

"awk '$1 == "rc" { print $2; }'" reads from standard input and, for any row where column 1 is "rc" (removed but still configured), outputs the value in column 2 (the package name).

aptitude is an alternate way to run apt-get with a slightly different command syntax and some differences in functionality that many of us prefer. This full command line:
```
sudo aptitude purge $(dpkg -l | awk '$1 == "rc" { print $2; }')
```
takes the output from the 'dpkg -l ...' command line (that what the $(...) part means) and uses it as command line arguments for the command 'sudo aptitude purge', which results in aptitude purging the configuration files for the packages listed by the 'dpkg -l ...' command line.

---

### Post by da burger on 2010-01-15
Thanks a lot. I appreciate your help.

---

