---
title: "system resource monitoring command"
date: 2010-04-14
forum: New to Ubuntu
---

### Post by siteregsam on 2010-04-14
hi,
  
   I am looking for Linux commands to get CPU & memory usage (that should be commonly available in all Linux platforms). For memory usage i found "*free -m*". After googling i found "*top*" to get CPU usage stat. But i need a command to show CPU usage in %. In ubuntu i had installed "**sysstat**" which solves my problem. But is there a similar command that will be available on all Linux to give me CPU usage as "**sysstat**"?

Thanks in advance.

---

### Post by Sepiraph on 2010-04-14
Go to System -> Admin -> System Monitor ... it will show CPU & memory resource but it doesn't show CPU temperature!

---

### Post by mbzn on 2010-04-14
Try TOP or HTOP

---

### Post by siteregsam on 2010-04-14
But I am actually looking for command as i have to write the Memory and CPU usage statistics to a text file. 

"TOP" will work until we give 'q' asking it to stop monitoring. This make writing the output to a file little odd. I need a command something like "free -m" for CPU usage. 

Anyway thanks for all ur replies....

---

### Post by yota on 2010-04-14
> **siteregsam said:**
> Thanks. But I am actually looking for commands as i have to write the Memory and CPU usage statistics to a text file.

then you should have a look at /proc/stat and /proc/meminfo (or other files in /proc) which are already text files containing what you are looking for.

To decode the criptic presentation of /proc/stat look [here]("http://www.linuxhowtos.org/System/procstat.htm")

---

### Post by siteregsam on 2010-04-14
Thanks yota :)

I am  working on a project in which i have to send the client machine load(CPU and memory info) information to a server. So i planned to run a script that will create a text file and append the info obtained by "cat /proc/stat and cat /proc/meminfo". 

Do u know any links to help me with the issue of writing scripts to perform above task?

---

### Post by yota on 2010-04-14
I suppose that basic bash scripting proficiency could come handy for this task.
You can start at the the linux documentation project [bash howto]("http://tldp.org/HOWTO/Bash-Prog-Intro-HOWTO.html").

A very simple one-liner can be this:
```

head -n1 /proc/stat |cut -d' ' -f3

```
where "head" picks the first line (-n1) and "cut" selects the third field (-f3) in a separated-by-spaces sequence (-d' ').

Adjusting the two numbers you can choose any single value from the matrix.

Hope this helps!

p.s. if you are interested in remote monitoring the resources of a linux box don't forget that there are tons of excellent foss tools already made.

---

### Post by siteregsam on 2010-04-14
Thanks Yota. 

If possible suggest me some tools that are good in monitoring remote linux machines...

---

### Post by yota on 2010-04-15
If you are interested in monitoring resources I like [munin]("http://munin-monitoring.org/") because it's web-based, straightforward and easily extensible (demo [here]("http://munin.ping.uio.no/ping.uio.no/index.html"))

If the service monitoring perspective is better for your needs then maybe [monit]("http://mmonit.com/monit/") could be an interesting tool.
But also [nagios]("http://www.nagios.org/") for network and others like [zabbix]("http://www.zabbix.com/") come to mind.

The list is far longer, as usual google is your friend!

Also don't forget to have a look at [landscape]("http://www.canonical.com/projects/landscape") which is the official tool endorsed by canonical (not free though).

---

