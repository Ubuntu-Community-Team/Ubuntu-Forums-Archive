---
title: "Bash floating point arithmetic?"
date: 2011-05-26
forum: New to Ubuntu
---

### Post by Dubslow on 2011-05-26
Hey guys, I've noticed that $(( do math here )) only carries integer results. Is there any way that I can get echo $((3/2)) to print "1.5" instead of "1" without using something like bc?
-Dubslow

---

### Post by nickleboyblue on 2011-05-26
Not sure how to do that in bash.  If it's just math you're doing, use python, which works as a VERY nice calculator if you know the basics of the syntax.  If you're echoing it so that you can save it in a file using some other tool, I can't help you there.

---

### Post by gmargo on 2011-05-26
You could use **perl** or **awk** fairly simply.

```

#!/bin/sh

num=3
denom=2

outa=$(awk "BEGIN{print $num/$denom}")
outp=$(perl -e "print $num/$denom")

echo "awk=$outa perl=$outp"

``````

$ sh divtest.sh
awk=1.5 perl=1.5

```

---

### Post by m_duck on 2011-05-26
Or you can pipe it into ***bc*** (it may need installing).

```
somevar=$(echo "scale=2; 15/2.8" | bc -l)
echo $somevar
```

Where scale=2 defines the number of decimal places your result should have.

---

### Post by roololing on 2011-06-22
> **Dubslow said:**
> Hey guys, I've noticed that $(( do math here )) only carries integer results. Is there any way that I can get echo $((3/2)) to print "1.5" instead of "1" without using something like bc?
-Dubslow
This function I used uses bc:
```
float_eval() {
    local stat=0
    local result=0.0
    if [ $# -gt 0 ]; then
        result=$(echo "scale=$float_scale; $*" | bc -q 2>/dev/null)
        stat=$?
        if [ $stat -eq 0  ]&&[ -z "$result" ]; then stat=1
    fi
    fi
    echo $result
    return $stat
}
```
Then for all equations that involve fractions, instead of $(( do math here )), you write it $(float_eval "do math here").
If you don't want to use bc then I think awk is the best way to go. I don't know anything about awk though, sorry.
I got the function from [this page]("http://www.linuxjournal.com/content/floating-point-math-bash"), which also has a function for using floats in conditionals.

---

### Post by Dubslow on 2011-06-22
Well, no one's presented a way to do it without bc or awk or perl or something besides bash, so I ended up doing 
$(echo "scale=10; 1000000000 * ($start-end+1) / $(timer $t $dt -u)" | bc)
in this particular script I was doing.

---

### Post by roololing on 2011-06-22
Yeah, bash isn't really great for doing math. I started with c/c++ so I freaked out when I realized there were no floats. :P

---

