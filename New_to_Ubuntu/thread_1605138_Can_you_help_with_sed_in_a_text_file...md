---
title: "Can you help with sed in a text file.."
date: 2010-10-24
forum: New to Ubuntu
---

### Post by hopelessone on 2010-10-24
Hi,

How can I sort out a text file,

>   6A Allgo Auto Electrical 
  33 Egerton St, Southport QLD 4215 
  (07) 5531 0505 
    
  A And A Auto Electrics 
  Boronia Heights QLD 4124 
  (07) 3800 2794 

so it looks like this:
> A And A Auto Electrics, Boronia Heights, QLD, 4124 ,(07) 3800 2794

so i can import it into a database,

Thanks,

Thanks,

---

### Post by SuaSwe on 2010-10-24
Do you mean that you want the script to sort line 4, 5 and 6 of whatever file it's applied to and arrange them on one line?

---

### Post by SuaSwe on 2010-10-24
If the file(s) will always be in that format, you could do:

```
 
sed 4q filename | tr '\n' ','

```

... which will select only line 4 onwards and replace line breaks with ",".

---

### Post by hopelessone on 2010-10-24
yes, there's 700 address like the sample given

---

### Post by SuaSwe on 2010-10-24
My apologies, I see what you mean now. Don't know off-hand but looking into it...

---

### Post by hopelessone on 2010-10-24
Hi,

```
sed 4q 1.txt | tr '\n' ',' > h.txt
```

looks like:

>   A Accel Auto Electrics 
,  6 / 41 Egerton St, Southport QLD 4215 
,  0418 757 778 
,    
,

---

### Post by SuaSwe on 2010-10-24
Yeah, I didn't realise your file had more than 6 lines, so it's moot anyway. :D

Try this:

```

cat filename | awk 'NR%4 != 0' | awk '{n2=n1;n1=n;n=$0;if(NR%3==0){printf"%s,%s,%s\n",n2,n1,n}}'

```

NB: this relies on your file being in the format you presented in the opening post, e.g. 3 address lines with a line break between.

---

### Post by hopelessone on 2010-10-24
>   A Accel Auto Electrics 
,  6 / 41 Egerton St, Southport QLD 4215 
,  0418 757 778 
  3A Acelaw/Dillon Car Clinic 
,  326 Millers Rd, Underwood QLD 4119 
,  (07) 3841 5722 
  4A Action Auto Electrical 
,  57 Lower West Burleigh Rd, Burleigh Heads QLD 4220 
,  (07) 5535 9311 

in the mean time i'll keep trying ...

---

### Post by SuaSwe on 2010-10-24
You don't have an erroneous line at the top of the file or anything, do you? 

Here's what I did and the results:

vim tmp

```

user@lx$ cat tmp
6A Allgo Auto Electrical
33 Egerton St, Southport QLD 4215
(07) 5531 0505

A And A Auto Electrics
Boronia Heights QLD 4124
(07) 3800 2794

B And A Auto Electrics
Boronia Lows QLD 4124
(07) 3800 1234


user@lx$ cat tmp | awk 'NR%4 != 0' | awk '{n2=n1;n1=n;n=$0;if(NR%3==0){printf"%s,%s,%s\n",n2,n1,n}}'
6A Allgo Auto Electrical,33 Egerton St, Southport QLD 4215,(07) 5531 0505
A And A Auto Electrics,Boronia Heights QLD 4124,(07) 3800 2794
B And A Auto Electrics,Boronia Lows QLD 4124,(07) 3800 1234
user@lx$

```

On the other hand, when I mistakenly left a line in at the top, I got:

```

user@lx$ cat tmp | awk 'NR%4 != 0' | awk '{n2=n1;n1=n;n=$0;if(NR%3==0){printf"%s,%s,%s\n",n2,n1,n}}'
user@lx$ vim tmp [<= that there was the erroneous line!] ,6A Allgo Auto Electrical,33 Egerton St, Southport QLD 4215
,A And A Auto Electrics,Boronia Heights QLD 4124
,B And A Auto Electrics,Boronia Lows QLD 4124

```

As noted, the script line relies on your file looking *exactly* as you presented it, e.g. without any blank lines at the start, for example.

---

### Post by hopelessone on 2010-10-25
hi,

there's something weird going on;
> Accel Auto Electrics   
,6 / 41 Egerton St, Southport QLD 4215 
,0418 757 778 
Acelaw/Dillon Car Clinic 
,326 Millers Rd, Underwood QLD 4119 
,(07) 3841 5722 
Action Auto Electrical 
,57 Lower West Burleigh Rd, Burleigh Heads QLD 4220 
,(07) 5535 9311 
Alian Auto Electrics Pty Ltd 
,1497 Ipswich Rd, Rocklea QLD 4106 
,(07) 3277 1999 

---

### Post by hopelessone on 2010-10-25
OK works,

What had happened is I saved it in gedit under Windows instead of Linux..

Thanks so much for the help...!

---

