---
title: "Bash script export to text file is blank"
date: 2010-10-15
forum: New to Ubuntu
---

### Post by fatality_uk on 2010-10-15
Pretty sure I am missing something simple, but could this be sanity checked please? Should output to a text file in the same directory


```
#!/bin/bash
for ((n=0 ; n < 255 ; n+=1))
do
	ip=192.168.1.$n
	if ping -c 1 -w 1 $ip
		then
			host=&ip
			$host >> hostStatus.txt
	fi
done
```

---

### Post by luvshines on 2010-10-15
```
host=$ip
echo $host >> hostStatus.txt
```

---

### Post by fatality_uk on 2010-10-15
[IMG]http://images.free-extras.com/pics/d/doh_homer_simpson-1084.jpg[/IMG]

---

### Post by fatality_uk on 2010-10-15
I know it's marked solved but just a follow up please.
In this loop, I want to add a
```
arp -na **ip**
```
lookup to the output line so I have a list of MAC addresses. Is this possible?

---

### Post by luvshines on 2010-10-15
> **fatality_uk said:**
> 
In this loop, I want to add a
```
arp -na **ip**
```
lookup to the output line so I have a list of MAC addresses. Is this possible?

Something like this ?
```

if ping -c 1 -w 1 $ip;then
  host=$ip
  macInfo=`arp -na $ip`
  echo "Host: $host, with MAC info: $macInfo" >> hostStatus.txt
fi
```

---

### Post by fatality_uk on 2010-10-15
That should do it, many thanks guys/girls

---

### Post by luvshines on 2010-10-15
If you are not using any of those(host, macInfo) variables for any other purpose but only echoing to file, you can also get away without using any

```

if ping -c 1 -w 1 $ip;then
  echo "Host: $ip, with MAC info: `arp -na $ip`" >> hostStatus.txt
fi

```

PS: Guy it is :D

---

### Post by fatality_uk on 2010-10-15
> **luvshines said:**
> If you are not using any of those(host, macInfo) variables for any other purpose but only echoing to file, you can also get away without using any

```

if ping -c 1 -w 1 $ip;then
  echo "Host: $ip, with MAC info: `arp -na $ip`" >> hostStatus.txt
fi

```

PS: Guy it is :D

Guy it is :)

Cheers.

---

