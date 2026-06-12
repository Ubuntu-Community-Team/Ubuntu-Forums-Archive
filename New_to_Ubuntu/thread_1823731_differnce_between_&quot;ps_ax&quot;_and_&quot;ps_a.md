---
title: "differnce between &quot;ps ax&quot; and &quot;ps ax &amp;&quot;"
date: 2011-08-12
forum: New to Ubuntu
---

### Post by manish411 on 2011-08-12
What is the difference when I run 
```

  ps ax

```

and 

```

 ps ax &

```

---

### Post by BitJunkie on 2011-08-12
The "&" tells the shell to run a command in the background, i.e. you don't have to wait for the command to complete before getting back to a prompt. If you run
```
sleep 10 &
```you should get a prompt back almost immediately (along with a process ID). If you then do a ps, you will see the sleep command is still running.

---

### Post by papibe on 2011-08-12
> **BitJunkie said:**
> The "&" tells the shell to run a command in the background, i.e. you don't have to wait for the command to complete before getting back to a prompt.
+1

It is very easy to understand with a command that takes more time. Try this:
```
$ sleep 5
```
And then:
```
$ sleep 5 &
```
Hope it helps,
Regards.

---

