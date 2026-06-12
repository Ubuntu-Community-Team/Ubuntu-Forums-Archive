---
title: "request for help with simple bash code"
date: 2011-02-06
forum: New to Ubuntu
---

### Post by Old Jimma on 2011-02-06
Hi Ubuntu Community:

I used photorec to recover many files, and it created many directories named:

ph.1
ph.2
...
ph.569

I used to be a good unix programmer but forgot mostly everything I know.

I want bash code that loops thru the directory names lised above, and copies all jpg files in each to a directory called /putithere

I think that the code might look like:

for i in 1 to 569
cd ph.$i
cp *.jpg /putithere
cd ..
end

Can somebody check this and make corrections, if necessary?

Thanks!
Phil Smith
Duluth, GA

---

### Post by DaithiF on 2011-02-06
almost ... your for syntax isn't quite right, there is no for x in y to z in bash, instead you could use:
for i in {1..659}

also, not really necessary to cd into each directory, instead:
```
for i in {1..659}
do
cp ph.$i/*.jpg /putitthere
done

```

and slightly more generically:
```
for i in ph.*/
do
cp $i/*.jpg /putitthere
done

```

---

### Post by Old *ix Geek on 2011-02-06
Also, is it possible that different directories can have files with identical names? If so, you'll want to account for that in the copying process by assigning a unique name to each file. You could tack on a number that incrementally increases, or use output from 'date' instead.

---

### Post by Old Jimma on 2011-02-06
Thank you for your replies!

Who would I account for the possibility that files in different directories may have the same name?

Thanks, 
Phil

---

