---
title: "Replace double forward slash with single slash"
date: 2009-03-17
forum: New to Ubuntu
---

### Post by runder on 2009-03-17
I'm working on a bash script to replace a double slash from a variable to a single slash

PATH="/one/two//three/four//five//six/seven//"

In the end, I want my PATH variable to contain the same thing but with the double forward slash replaced by a single.

PATH="/one/two/three/four/five/six/seven/"

Any feedback is appreciated :)

I tried 
PATH=`echo ${PATH//\/\//\/}`
but it doesn't always work... Sometimes in my path, I use other variables.. maybe that's why it doesn't work
(i.e. PATH="$A/$B/three//four/$C/$D)

---

### Post by runder on 2009-03-17
Well, I solved this with a function

```

function fixPath()
{
        local inputVar=$1
        local varValue=${!1}
        eval $1=${varValue//\/\//\/}
}

PATH='/one//two//three/four/five'
fixPath PATH

```

I still think it's ugly, but it works  :popcorn:

---

### Post by durand on 2009-03-17
You could try sed.

```
echo $PATH | sed 's,//,/,g'
```

The , are used to separate the different options. The s and g tell it to replace all the instances of // with /, I think...

---

### Post by kaibob on 2009-03-17
> **runder said:**
> I'm working on a bash script to replace a double slash from a variable to a single slash...

You can also use tr:

```
echo /one/two//three/four//five//six/seven// | tr -s /
```

---

### Post by ghostdog74 on 2009-03-17
don't need to call external command, in bash
```

# a="/one/two//three/four//five//six/seven//"
# echo ${a//\/\//\/}
/one/two/three/four/five/six/seven/


```

---

### Post by durand on 2009-03-18
But that looks soo ugly :o

---

### Post by ghostdog74 on 2009-03-18
> **durand said:**
> But that looks soo ugly :o
that ugliness saves you one external process.

---

### Post by durand on 2009-03-18
I suppose it depends on whether you want clean or efficient code...Not that you can't have a balance of both.

---

