---
title: "Perl printing the match, NOT the whole line"
date: 2010-07-30
forum: New to Ubuntu
---

### Post by B34ST1Y on 2010-07-30
Hi everyone. I am writing a perl script that goes through a file and prints the occurrence of a particular regex.


A code snippet of it: ```
$data = `type content.html | grep @`;	

	if ($data =~ m! \S.+\@.+\.com!) 
			{
		#	$data = /\s.+\@.+\.com/gm;
			print ("matched * $1 * \n");
			}
```


When I run it, it can successfully do something if it matches it, but I can't get it to print out what it matched :( . Any Perl guru's out there, I would be extremely thankful :)

---

### Post by ghostdog74 on 2010-07-30
You are using Perl on a windows machine right? (judging from the command "type". ) If you are using Perl, then use Perl. There is no need to call DOS commands.

```

perl -e 'print if /<your expression here>/' file

```
or iterate the file line by line
```

while (<>){
  chomp;
  if ($_ =~ /@/ ){
     # do something.
  }
}

```

---

### Post by RiceMonster on 2010-07-30
Put parentheses arround your expression so you can have $1 contain the first match. Remember, parentheses = match. You can also use parentheses in specific parts of your espression to only match certain parts.

```
if ($data =~ /(\S.+\@.+\.com)/) {
    print qq/matched * $1 * \n/;
}
```

---

