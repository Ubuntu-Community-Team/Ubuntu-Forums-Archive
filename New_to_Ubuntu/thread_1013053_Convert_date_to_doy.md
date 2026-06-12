---
title: "Convert date to doy"
date: 2008-12-16
forum: New to Ubuntu
---

### Post by aabrego on 2008-12-16
Hello:

I have a script that requires the use of DOY (as a variable) instead of YY/MM/DD. I already obtained these parameters from the downloaded files and stored them as variables (i.e. $day, $month, $year).

Is there any simple script that I could incorporate in mine to do this job?

Regards,

Antonio

---

### Post by mbsullivan on 2008-12-16
You should be able to obtain this by taking the following steps:

(1) Print the date (in MM/DD/YY or any other valid format) to STDOUT
(2) Pipe this to the "date" program, with the following options:

```
[output] | date --date=$1 +%j
```

For example, the following code prints the current date as a DOY. Just substitute your variables on the LHS, and you'll be good to go:

```
echo "12/16/08" | date --date=$1 +%j
```

Mike

PS: Note that "date" is smart enough to handle leap years, so the number it returns is in the range [0,366]. Don't let this mess up whatever program you're redirecting the DOY to!

---

### Post by aabrego on 2008-12-16
Hi Mike:

Just one more question. I was able to get the DOY. I included in my script by making the following:

$comm = "date -d $year-$month-$day +%j";
system("$comm");

However, at the end of the day I need to get the answer, 351 for instance, as a variable. I sorry but I am new at linux.

Regards,

---

### Post by mbsullivan on 2008-12-16
Hi aabrego,

What scripting language are you using??? There are many.

Mike

---

### Post by aabrego on 2008-12-16
This particular program is being written in perl.

---

### Post by mbsullivan on 2008-12-16
> This particular program is being written in perl.

See [here]("http://www.devdaily.com/perl/edu/articles/pl010004.shtml").

I'm jumping on a plane. Let me know if you need any more help, but it may take me a while to get back to you.

Mike

---

### Post by aabrego on 2008-12-17
Thank you very much Mike. The link turned out to be very useful.

Regards,

Antonio

---

