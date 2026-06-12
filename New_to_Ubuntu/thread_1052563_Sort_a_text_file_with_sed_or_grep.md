---
title: "Sort a text file with sed or grep?"
date: 2009-01-27
forum: New to Ubuntu
---

### Post by hammer v2 on 2009-01-27
Hi guys, 
I'm not a total beginner but this one has got me stumped. I have a text file with lots of words seperated by commas...

eg..

avahi, beard, green, blue, avahi, red, blue, blue, avahi

I need to find some way of listing only the words that occur 3 times. I'm guessing sed, grep or awk would be the go here...but I haven't got the faintest idea on how to use them to do this.

Anyone of you CLI ninjas care to show me how to do it?

---

### Post by sdennie on 2009-01-27
Try:

```

#!/usr/bin/perl

my $NUM_TIMES=3;
my %count;

while(<>)
{
    split /\s*\,\s*/;
    $count{$_}++ for @_;
}

for(keys %count)
{
    print "$_\n" if $count{$_} >= $NUM_TIMES;
}

```

---

### Post by hammer v2 on 2009-01-27
That's it! Thank you very much sdennie!

---

