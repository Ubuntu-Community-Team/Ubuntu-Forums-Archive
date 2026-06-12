---
title: "Confirmation of a command ${var:-&quot;value&quot;}"
date: 2010-02-11
forum: New to Ubuntu
---

### Post by RavUn on 2010-02-11
I'm looking through a script and see things like:
```
JBOSS_CONF=${JBOSS_CONF:-"default"}
```
and
```
JBOSS_BIND_ADDR=${JBOSS_HOST:+"-b $JBOSS_HOST"}
```

I'd like to confirm that my thoughts of what they're doing are correct.  I haven't been able to find anything in google and I can't google symbols.

Does ```
VAR=${VAR:-"value"}
``` assign value to VAR if VAR is null and ```
VAR_A=${VAR_B:+"option"}
``` assign VAR_B plus "option" to VAR_A?

Thanks.

---

### Post by mobilediesel on 2010-02-11
> **RavUn said:**
> I'm looking through a script and see things like:
```
JBOSS_CONF=${JBOSS_CONF:-"default"}
```
and
```
JBOSS_BIND_ADDR=${JBOSS_HOST:+"-b $JBOSS_HOST"}
```

I'd like to confirm that my thoughts of what they're doing are correct.  I haven't been able to find anything in google and I can't google symbols.

Does ```
VAR=${VAR:-"value"}
``` assign value to VAR if VAR is null and ```
VAR_A=${VAR_B:+"option"}
``` assign VAR_B plus "option" to VAR_A?

Thanks.

Pretty close, check here: [http://www.linuxjournal.com/article/8919](http://www.linuxjournal.com/article/8919)
for a good explanation.
> Operator: ${foo:-bar}
Function: If $foo exists
and is not null, return $foo. If it doesn't exist or is null,
return bar.

Example:

```
$ export foo=""
$ echo ${foo:-one}
one
$ echo $foo

$
```
> Operator: ${foo:+bar}

Function: If $foo exists and is not null, return bar. If it doesn't exist
or is null, return a null.

Example:

```
$ export foo="this is a test"
$ echo ${foo:+bar}
bar
$
```

---

### Post by gmargo on 2010-02-11
> **RavUn said:**
> 
```

JBOSS_CONF=${JBOSS_CONF:-"default"}
JBOSS_BIND_ADDR=${JBOSS_HOST:+"-b $JBOSS_HOST"}
```

It is documented in the **bash** man page.  Also, here is the **bash** reference manual link (which seems to be the same text as the man page):
[http://www.gnu.org/software/bash/manual/bashref.html#Shell-Parameter-Expansion](http://www.gnu.org/software/bash/manual/bashref.html#Shell-Parameter-Expansion)

${parameter:-word}
Use Default Values.  If parameter is unset or null, the expansion of word is substituted. Otherwise, the value of parameter is substituted.

${parameter:+word}
Use Alternate Value.  If parameter is null or unset, nothing is substituted, otherwise the expansion of word is substituted.

---

