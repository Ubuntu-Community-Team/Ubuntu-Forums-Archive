---
title: "If-statement in Bash script"
date: 2009-03-26
forum: New to Ubuntu
---

### Post by Ralph_Donnchadh on 2009-03-26
Hello,

I am new to Ubuntu, and I am trying to write my first shell script. 
I know in C++ I can use the following if-statment

```
// for some integers a and b
if (!( (a == 1) &&(b == 2)) )
{
	// Do something
}
```

I also found out that in shell script I can use the following to achieve the same effect.

```
# for some integers a and b
if [ ! a -eq 1 ] || [! b -eq 2 ]	# Difficult to read
then
	# Do something
fi
```

However, in the shell script example, the condition statement is difficult to read. Is there any way in shell script to write the condition as:

(! (condition1 && condition2) )

to improve readability?

Thanks

---

### Post by KIAaze on 2009-03-26
```
#!/bin/bash
# for some integers a and b
a=1
b=2
echo "a=$a and b=$b"
if ! [ $a -eq 1 ] || ! [ $b -eq 2 ]     # Difficult to read
then
        # Do something
        echo "not(a=1) or not(b=2)"
fi

if ! ( [ $a -eq 1 ] && [ $b -eq 2 ] )   # Difficult to read
then
        # Do something
        echo "not(a=1 and b=2)"
fi

a=3
b=3
echo "a=$a and b=$b"
if ! [ $a -eq 1 ] || ! [ $b -eq 2 ]     # Difficult to read
then
        # Do something
        echo "not(a=1) or not(b=2)"
fi

if ! ( [ $a -eq 1 ] && [ $b -eq 2 ] )   # Difficult to read
then
        # Do something
        echo "not(a=1 and b=2)"
fi

```

You might also want to look at the man page for test:
```
man test
```

---

### Post by Ralph_Donnchadh on 2009-03-26
Thanks KIAaze! Your examples help a lot!

---

### Post by ibuclaw on 2009-03-26
tbh, to a small degree, bash can be as readable as you want it to be...
```

#!/bin/bash

function eq
{
    [ $1 -eq $2 ]
    return $?
}

a=3;
b=3;

if (eq $a 3) && (eq $b 3)
then
    printf "\$a and \$b are both equal to 3\n";
fi

```
But that doesn't mean that it is readable for others.

IMO ... Perl is a better language for Swiss Army Knife jobs in Linux than what Bash is.
```

#!/usr/bin/perl

use strict;
use warnings;

my ($a, $b) = (3, 3);

if($a == 3 or $b == 3)
{
    print "\$a and \$b are both equal to 3\n";
}

# Alternate Syntax
print "\$a and \$b are both equal to 3\n" if($a eq 3 and $b eq 3);

```

Regards
Iain

---

