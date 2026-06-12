---
title: "if statement logic error"
date: 2011-03-02
forum: New to Ubuntu
---

### Post by pvictory on 2011-03-02
> 
[INDENT]Hello, I seem to have a logic error that I just can't figure out. When I run this simple program by entering in a number and click submit it should return a letter grade. The problem is it will only return "E" no matter what numbers I input. Can someone please show me what I'm missing in my code so it does run straight to the bottom. Thank you
[/INDENT]
 
```

[FONT=Courier New]<form action="new5.php" method="get">[/FONT]
[FONT=Courier New] <input type="text" name="lettergrade"><br>[/FONT]
[FONT=Courier New] <input type="Submit">[/FONT]
[FONT=Courier New]</form>[/FONT]
[CODE]

```
[FONT=Courier New]<body>[/FONT]
[FONT=Courier New]<?php[/FONT]
[FONT=Courier New] $lettergrade = $_POST['lettergrade'];[/FONT]
 
 
 
[FONT=Courier New]    if($lettergrade >= "92"){[/FONT]
 
[FONT=Courier New]       echo "A <br/>";[/FONT]
[FONT=Courier New]    }[/FONT]
[FONT=Courier New]    elseif[/FONT]
[FONT=Courier New]       ($lettergrade >= "84"){[/FONT]
 
[FONT=Courier New]        echo "B <br/>";[/FONT]
[FONT=Courier New]    }[/FONT]
[FONT=Courier New]    elseif[/FONT]
[FONT=Courier New]       ($lettergrade >= "76"){[/FONT]
 
[FONT=Courier New]       echo "C <br/>";[/FONT]
[FONT=Courier New]    }   [/FONT]
[FONT=Courier New]    elseif[/FONT]
[FONT=Courier New]        ($lettergrade >= "68"){[/FONT]
 
[FONT=Courier New]       echo "D <br/>";[/FONT]
[FONT=Courier New]    }[/FONT]
 
[FONT=Courier New]    else{[/FONT]
 
[FONT=Courier New]       echo "E <br/>";[/FONT]
 
 
[FONT=Courier New]}[/FONT]
 
 
 
[FONT=Courier New]?>[/FONT]
[FONT=Courier New]</body>[/FONT]
[FONT=Courier New]</html>[/FONT]
[/CODE]

---

### Post by jwcalla on 2011-03-02
Could be the quotes around the numbers.  Try it without the quotes.

---

### Post by d4rk on 2011-03-02
In C++, the double quotation marks denotes the content as being a string literal. As jwcalla already mentioned, this is probably the issue.

---

### Post by asmoore82 on 2011-03-02
I know nothing of PHP&#8230;

But I assume the other posts are correct that the quotes are creating literal strings.

I also assume that PHP would never automatically convert the user input to
an integer format, so working with strings would be the correct goal.

So perhaps PHP doesn't directly support the >= operator on strings.

EDIT: Quick googling has shockingly revealed to me that PHP apparently does do
implicit type conversion in comparisons. However, to force true string comparison,
use the strcmp() function; for case insensitivity, use strcasecmp().
[http://www.brainbell.com/tutorials/php/Comparing_Strings.htm](http://www.brainbell.com/tutorials/php/Comparing_Strings.htm)

---

### Post by jwcalla on 2011-03-02
I only know a little bit of PHP but IIRC if a variable is not explicitly typecast it can take any form, and PHP only converts it to a type when it's used as a particular type would be.  So it could probably be used as an integer in this case.

---

### Post by pvictory on 2011-03-02
> 
Hi, I have tried it without quotes also and it still doesn't work. I have tried several different methods and it still runs the same way. It's almost like I need a break statement between the if statements but I know you can only use that in a case statement. I added the double quotes out of frustration knowing it's part of C programming because that is also one of the classes I have taken. Please if you have another suggestion please let me know.

```

 
<body>
<?php
 $lettergrade = $_POST['lettergrade'];
 
 
 
  if($lettergrade >= 92){
  
   echo "A <br/>";
  }
  elseif
   ($lettergrade >= 84){
 
      echo "B <br/>";
  }
  elseif
   ($lettergrade >= 76){
   
   echo "C <br/>";
  } 
  elseif
      ($lettergrade >= 68){
  
   echo "D <br/>";
  }
  
  else{
       
   echo "E <br/>";
  
}
 
 
  
?>
</body>
</html>

```

---

### Post by jwcalla on 2011-03-02
I would echo out your $lettergrade variable first to make sure it's coming in good, and if it is, try converting it to an integer:

```

$lettergrade = intval($_POST['lettergrade']);
```

---

### Post by pvictory on 2011-03-02
> Hi again, I'm not sure if I'm following what you are saying. What this program does is convert a number to a letter grade. I can run it and get a letter grade but I only get an (E) grade no matter what number I enter. So lets say I enter the number 99 it still gives me and E instead of an A. Please advise. 
 
```
form action="new5.php" method="get">
 <input type="text" name="lettergrade"><br>
 <input type="Submit">
</form>
 
 
<body>
<?php
 $lettergrade = $_POST['lettergrade'];
 
 
 
  if($lettergrade >= 92){
  
   echo "A <br/>";
  }
  elseif
   ($lettergrade >= 84){
 
      echo "B <br/>";
  }
  elseif
   ($lettergrade >= 76){
   
   echo "C <br/>";
  } 
  elseif
      ($lettergrade >= 68){
  
   echo "D <br/>";
  }
  
  else{
       
   echo "E <br/>";
  
}
 
 
  
?>
</body>
</html>

```

---

### Post by jwcalla on 2011-03-02
If the value coming in from the user is a string literal -- which is a very likely possibility -- then you're not going to be able to make comparisons using the >= operator.  You can't compare a string to an integer (at least, not logically).

If indeed the value is being represented as a string, you'll have to first convert it to an integer using the intval() function, and then make the comparisons on the integer value.

---

### Post by d4rk on 2011-03-02
I assume there's no way to explicitly define the variable lettergrade as to be of an integer datatype? As this would probably make the implementation treat the input as thus...

Edit: You could try the function is_int, or what about initializing the variable by assigning it an integer value? Like: $variable = 0;

Edit2: Wouldn't a PHP-forum be a more appropriate place to ask for help regarding PHP-issues? ;-)

---

