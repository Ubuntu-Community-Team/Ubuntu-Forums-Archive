---
title: "create a variable and print it into a file"
date: 2010-11-28
forum: New to Ubuntu
---

### Post by Peter.Paul on 2010-11-28
Hello,

I am trying to calculate an average value and write it into a file. The calculation of the average works perfect, but it seems like, I cannot put it on a variable and print it out.

So, this works perfect
```
awk 'BEGIN{total=0;} {total+=$1} END{printf (total/50)}' $1tail.txt >> temp.txt
```And this one does not:
```
variable = awk 'BEGIN{total=0;} {total+=$1} END{printf (total/50)}' $1tail.txt >> temp.txt
echo "$variable is the average. The highest value is $high"

```Can you help me out with this?

---

### Post by zipteye on 2010-11-29
Maybe this.
 
```

 
variable = awk 'BEGIN{total=0;} {total+=$1} END{printf (total/50)}' 
 
variable $1tail.txt >> temp.txt
 
echo "$variable is the average. The highest value is $high"

```

---

### Post by Peter.Paul on 2010-11-30
this script gives me the error message "variable not found".

---

### Post by zipteye on 2010-11-30
variable = ` awk "BEGIN{total=0;} {total+=$1} END{printf (total/50)}" `

Try that.

---

