---
title: "Help with Launcher Command Error"
date: 2010-01-20
forum: New to Ubuntu
---

### Post by egruber on 2010-01-20
For skype, I was advised by their website to launch it with the command:

LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype 

This works when I use the Terminal.  But when I put it in the launcher I get:

Failed to execute child process "LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so" (No such file or directory)

I used Preferences/Main Menu/Internet/Skype then selected Properties and replaced the text Skype in the Command Box with the LD command typed above.  Did I do something wrong??

---

### Post by sisco311 on 2010-01-20
```
sh -c "LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype"
```

---

### Post by egruber on 2010-01-20
> **sisco311 said:**
> ```
sh -c "LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype"
```

I copied and pasted it exactly as written into the launcher and I didn't get an error.  So...I must assume the preload command executed?  I guess there is no way to tell.

Do you mind giving a brief explanation of the solution?  I would like to learn from this.

Thanks very much!!

---

### Post by sisco311 on 2010-01-20
LD_PRELOAD is an [environment variable]("http://en.wikipedia.org/wiki/Environment_variable"). 

If it's used in front of a program to run, the variables will be exported to the environment and thus appear as real environment variables to the program (in your case skype):

```
VARIABLE=value application_name
```

The launcher doesn't handle environment variables. In order to pass the variable to skype, you have to run the command in a sub-shell (sh or bash): 

```
sh -c "VAR=value command"
```

---

### Post by egruber on 2010-01-20
Great explanation!  Many thanks!

---

