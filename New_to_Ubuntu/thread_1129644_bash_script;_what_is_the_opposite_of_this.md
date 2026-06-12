---
title: "bash script; what is the opposite of this"
date: 2009-04-18
forum: New to Ubuntu
---

### Post by ant2ne on 2009-04-18
I'd like to add an entry for if the ping failed. What would that look like?


```
PingSERVERNAME()
{
echo Worked!!!
}
ping -c 1 SERVERNAME && PingSERVERNAME
```

---

### Post by click4851 on 2009-04-18
not a programmer yet, but I've written a few scripts. Could you use a timer statement. If no response within say 30 sec, pipes to a message indicating so.

---

### Post by click4851 on 2009-04-18
found this .....the -c count option could be used as well, talks about a unaswered ping toward the bottom, and how ping exits. Found it here...

[http://linux.die.net/man/8/ping](http://linux.die.net/man/8/ping)

---

### Post by sarang on 2009-04-18
You want something like this:

```

ping_server ()
{
  ping -c 1 "$1"
  return_value="$?"
  if [ "$return_value" != "0" ]

  then
       echo "Ping failed."
  else
       echo "Ping succeeded."
  fi
}

```

---

### Post by ant2ne on 2009-04-19
thanks sarang. That looks more complicated than my current scripting level. I like it though!!

---

### Post by hovzio on 2009-04-19
hi, this will work,

```
ping -c 1 server 2> /dev/null >&2 && echo "worked" || echo "it didnt work"
```

You can replace the echo commands with funktions if you like. The command following the || is only executed if the last exit status does not equal 0. You can also alias this command to a single server, or put it in a function :)

```
pingserver ()
{
ping -c 1 "$1" 2> /dev/null >&2 && echo "worked" || echo "it didnt work"
}

```

---

### Post by sarang on 2009-04-24
> **ant2ne said:**
> thanks sarang. That looks more complicated than my current scripting level. I like it though!!

By convention, programs return an exit status of zero upon successful planned exit and other non-zero exit status (often used as an errorcode to find problems) if an error is encountered. The last exit status is automatically assigned to the special variable $? by the shell. The bash function that I posted earlier just copies $? into $return_value for easy readability and then compares it to zero to determine success. (The != operator is 'not equal'). The use of quotes is analogous to casting everything as strings in real programming languages.

---

