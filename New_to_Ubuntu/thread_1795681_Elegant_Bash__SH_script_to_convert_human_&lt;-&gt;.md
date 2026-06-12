---
title: "Elegant Bash / SH script to convert human &lt;-&gt; bytes values?"
date: 2011-07-03
forum: New to Ubuntu
---

### Post by honeybear on 2011-07-03
Hello,

For SH/DASH, someone have already an elegant script that can handle such things? 

Or under AWK, for portability. [http://www.softpanorama.org/Tools/awk.shtml](http://www.softpanorama.org/Tools/awk.shtml) awk is underappreciated for coding and is very portable and universal

```
54.4M = 57042534 bytes
```



Any help would be welcome,

Thanks

---

### Post by honeybear on 2011-07-03
Enjoy !! 

>  echo "83498543893452" | awk '{ sum=$1 ; hum[1024**3]="Gb";hum[1024**2]="Mb";hum[1024]="Kb"; for (x=1024**3; x>=1024; x/=1024){ if (sum>=x) { printf "%.2f %s\n",sum/x,hum[x];break } }}'


---

### Post by nemesisgus on 2012-07-19
> **honeybear said:**
> Enjoy !!

Cool! Many thanks.

---

### Post by cleaudevink2 on 2012-10-04
Is there any way this command can be edited to display 0 if the value is too small? For example is you use 500 as input, the command gives no output.

---

