---
title: "Modifying .bash file"
date: 2010-08-18
forum: New to Ubuntu
---

### Post by newport_j on 2010-08-18
I want to permanetly change my path so I am editing my .bash file. However, when I gedit the file I see no specific line that pertains to the PATH. Is is okay to just put in a statement like one wuld put in in a command line like
 
 
export ....
 
I just want to add some additional paths to my path. What is the way to do it.
 
 
Newport_j

---

### Post by talonmies on 2010-08-18
There is .bashrc or .bash_profile for user shell customizations. Which are you editing?

---

### Post by satman-ga on 2010-08-18
I assume you mean you're editing .bashrc?

In that case you can add the following to the file

```
export PATH="$PATH:/some/dir:/some/other/dir"
```

---

### Post by newport_j on 2010-10-01
Yes, that is what I mean. Where is that line placed in the bash file?
 
Newport_j

---

### Post by talonmies on 2010-10-01
Anywhere you want that is syntactically valid for a shell script

---

### Post by satman-ga on 2010-10-01
I typically place my custom changes to the end of the file.

---

### Post by newport_j on 2010-10-01
Okay, I would think that something like what I write at the Ubuntu command line is syntactically valid. Such as:
 
export PATH="$PATH= ..."
 
Is that valid? 
 
Now what I put on the right hand side of the = sign is of course the new path. 
 
Newport_j

---

### Post by talonmies on 2010-10-03
No, that isn't valid. Just do

```

export PATH = $PATH:/your/additional/paths/go/here

```

This is explained in the bash man page and any one of the numerous tutorials on shell scripting and environment customization that google will find for you.

---

### Post by newport_j on 2010-11-02
I am wanting to edit another .bashrc file on another Ubuntu installation. Where is this .bashrc file located again?
 
 
Newport_j

---

