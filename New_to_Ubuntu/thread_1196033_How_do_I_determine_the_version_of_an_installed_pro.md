---
title: "How do I determine the version of an installed program?"
date: 2009-06-24
forum: New to Ubuntu
---

### Post by RobertL on 2009-06-24
The practical example is that a new version of foomatic was posted in April and I want to know if I am using that version.

---

### Post by oldos2er on 2009-06-24
```
apt-cache show [package name]
```

---

### Post by clive littlewood on 2009-06-24
Hi

Click the help tab and then click about, that will show you the version number

Clive

---

### Post by porchrat on 2009-06-24
A lot of programs have a "-version" option in the command line.

For example to check which version of java you are running:

```
java -version
```

---

### Post by llamabr on 2009-06-24
Everyone loses their complete mind when I suggest that you read the man page, but the version tag is most easily found there.  Most programs have it as --version, or -v, or -V

---

### Post by RobertL on 2009-06-24
> **clive littlewood said:**
> Hi

Click the help tab and then click about, that will show you the version number

Clive

> **porchrat said:**
> A lot of programs have a "-version" option in the command line.

For example to check which version of java you are running:

```
java -version
```

> **llamabr said:**
> Everyone loses their complete mind when I suggest that you read the man page, but the version tag is most easily found there.  Most programs have it as --version, or -v, or -V

These suggestions only apply to application programs. But as I say in the question, I'm trying to find the version of printing software. IOW a package or a device driver. There is no "tab" to click or "-v" to type.

---

### Post by Bachstelze on 2009-06-24
[http://packages.ubuntu.com/search?keywords=foomatic&searchon=names&suite=jaunty&section=all](http://packages.ubuntu.com/search?keywords=foomatic&searchon=names&suite=jaunty&section=all)

or [font="monospace"]dpkg -l | grep foomatic[/font].

---

### Post by RobertL on 2009-06-24
> **oldos2er said:**
> ```
apt-cache show [package name]
```

So far as I can see the command you give doesn't do the job. It shows the version number of the package in the repository, whether installed or not.  

But from the apt-cache man page I see there is an option "--installed" and the description says it limits the output to installed packages (something like that) but it doesn't seem to do that.

For example, "apt-cache --installed show hplip" gives information on hplip so I assume that means it thinks it is installed. But Synaptic Package Manager says hplip is not installed.

Can anybody shed light on the apparent conflict between Synaptic Package Manager and the apt-cache command?

---

### Post by Bachstelze on 2009-06-24
> **RobertL said:**
> So far as I can see the command you give doesn't do the job. It shows the version number of the package in the repository, whether installed or not.  

But from the apt-cache man page I see there is an option "--installed" and the description says it limits the output to installed packages (something like that) but it doesn't seem to do that.

For example, "apt-cache --installed show hplip" gives information on hplip so I assume that means it thinks it is installed. But Synaptic Package Manager says hplip is not installed.

Can anybody shed light on the apparent conflict between Synaptic Package Manager and the apt-cache command?

[quote=man apt-cache]       --installed
           Limit the output **of depends and rdepends** to packages which are currently installed. Configuration Item:
           APT::Cache::Installed.
[/quote]

of depends and rdepends, not show.

---

### Post by RobertL on 2009-06-24
> **HymnToLife said:**
> of depends and rdepends, not show.

Oh right! I read it too fast. Thanks.

---

