---
title: "bash for loop with int in iptables create error"
date: 2011-07-22
forum: New to Ubuntu
---

### Post by SpinningAround on 2011-07-22
How do you index an array in bash, the following code actually don't loop throw the array. Instead it simply print the full array on the first loop.

[PHP]
TCP_PORTS="80 443"

# TCP
for index in ${!TCP_PORTS[*]}
do
echo ${TCP_PORTS[$index]}
done
[/PHP]

EDIT
[PHP]
#!/bin/bash
for index in ${!TCP_PORTS[*]}
do
echo iptables -A INPUT -p tcp --dport 1024:65535 --sport ${TCP_PORTS[$index]} -m state --state ESTABLISHED,RELATED -j LOG $LOG_CONF ${TCP_LOG[$index]}
echo iptables -A INPUT -p tcp --dport 1024:65535 --sport ${TCP_PORTS[$index]} -m state --state ESTABLISHED,RELATED -j ACCEPT
done
[/PHP]

output
```

iptables -A INPUT -p tcp --dport 1024:65535 --sport 80 443 -m state --state ESTABLISHED,RELATED -j LOG --log-level 4 -m limit --limit 5/min --limit-burst 7 --log-prefix "http: " "https: "
iptables -A INPUT -p tcp --dport 1024:65535 --sport 80 443 -m state --state ESTABLISHED,RELATED -j ACCEPT

```

---

### Post by LemursDontExist on 2011-07-22
I might try:

```
TCP_PORTS="80 443"
array=($TCP_PORTS)
count=${#array[@]}
for index in `seq 0 $((count-1))`
do 
    echo ${array[$index]}
done
```

I'm not really a bash expert, so I imagine there's a more correct/elegant way to do this, but that seems to work for me.

---

### Post by sisco311 on 2011-07-22
If you want to use an array, then try:
```
PORTS=(80 443)
for port in "${PORTS[@]}"
do
    echo "$port"
done
```

See:
[http://mywiki.wooledge.org/BashGuide/Arrays](http://mywiki.wooledge.org/BashGuide/Arrays)

---

### Post by LemursDontExist on 2011-07-22
> **sisco311 said:**
> If you want to use an array, then try:
```
PORTS=(80 443)
for port in "${PORTS[@]}"
do
    echo "$port"
done
```

See:
[http://mywiki.wooledge.org/BashGuide/Arrays](http://mywiki.wooledge.org/BashGuide/Arrays)

That was my original idea too - but SpinningAround seems to be accessing a TCP_LOG array by index too (in his edit), so I assumed  he needed the index, and didn't necessarily have control of the input format for TCP_PORTS.  If these assumptions are wrong, this is better!

---

### Post by sisco311 on 2011-07-22
> **LemursDontExist said:**
> That was my original idea too - but SpinningAround seems to be accessing a TCP_LOG array by index too (in his edit), so I assumed  he needed the index, and didn't necessarily have control of the input format for TCP_PORTS.  If these assumptions are wrong, this is better!

Oh, I see, I think you are right. In that case something like:
```

arr=(1 2 3)
for i in "${!arr[@]}"
do
    echo "$i"
done

```

should do the trick.

If you don't mind I have a few comments on your code. :)

`COMMANDS` is not POSIX, the usage of the POSIX form: $(COMMANDS) is preferred.

Instead of seq you can use brace expansion: {0..10}, but you can't use variables inside the curly brackets, so in this case I would use a C style for loop:
```
for ((i=0; i<count; i++)); do
```

Oh, and ALWAYS quote your variables: *echo "${array[$index]}"*

---

### Post by LemursDontExist on 2011-07-22
> **sisco311 said:**
> Oh, I see, I think you are right. In that case something like:
```

arr=(1 2 3)
for i in "${!arr[@]}"
do
    echo "$i"
done

```

should do the trick.

If you don't mind I have a few comments on your code. :)

`COMMANDS` is not POSIX, the usage of the POSIX form: $(COMMANDS) is preferred.

Instead of seq you can use brace expansion: {0..10}, but you can't use variables inside the curly brackets, so in this case I would use a C style for loop:
```
for ((i=0; i<count; i++)); do
```

Oh, and ALWAYS quote your variables: *echo "${array[$index]}"*

Ahh!  That is much better =)  I knew there was a way to enumerate an array, but couldn't remember/find it, and didn't notice it in SpinningAround's original post.  

I write a bash script about every two months and always find myself relearning it all, but a little more sticks each time!  Many thanks for the notes!

---

### Post by SpinningAround on 2011-07-22
Thanks, it's working now :)

---

