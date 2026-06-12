---
title: "Using CSS or other to format instance of a specific word"
date: 2009-08-30
forum: New to Ubuntu
---

### Post by Trefethen on 2009-08-30
I need a way to format a specific word or sentence containing a specific word within a lot of text in a web page. I am not a programmer and would love it if there was a way to achieve this using CSS, so that whenever any new text is added to a new document associated with a certain style sheet, all instanced of a certain word would be automatically formatted in this way.

For example, in the text that follows the word "hope" appears. In this text I would like each instance of the word hope to be formatted in such a way as to call more attention to it, bold, larger, colored, etc.[INDENT]*With treatment, more than 80% of people with depression respond favorably to medications, and the feeling of hopelessness subsides. With treatment, most people are able to resume their normal work and social activities. Symptoms of a depressive disorder include at least five of the following changes in the individual's previous characteristics: loss of motivation and inability to feel pleasure; deep chronic sadness or distress; changes in sleep patterns; lack of physical energy (apathy); feelings of hopelessness and worthlessness; difficulty with concentration; overeating or loss of appetite; withdrawal from interpersonal interactions or avoidance of others; death wishes, or belief in his/her own premature death. In children, the first signs of depression may be irritation and loss of concentration, apathy and distractibility during classes, and social withdrawal. Some adults initially complain of constant fatigue, even after long hours of sleep, digestive disorders, headaches, anxiety, recurrent memory lapses, and insomnia or excessive sleeping. An episode of major depression may be preceded by a period of dysthymia, a mild but persistent low mood state, usually accompanied by diminished sexual drive, decreased affective response, and loss of interest in normal social activities and hobbies.*[/INDENT]

---

### Post by keplerspeed on 2009-08-31
You could use a custom tag. So in your style.css have:
```

div#content standout {
	font: 12px monospace;
		}

```
And then for each instance of the word in the file:
```

<standout>This text will feature the defined style in style.css <standout>

```

However, to do it automatically, im not sure.

---

### Post by Trefethen on 2009-08-31
Yeah that would seem to work. The main issues with this is the need to manually locate each instance of the word. Righ tnow I am doing a manual find replace in Dreamweaver. It would be ideal if the style sheet could format each instance of the word, in this case, hope.

---

### Post by achase79 on 2009-08-31
you may have to use javascript to find every instance and add formatting.
look up js slice, js search and js replace at w3schools.com

---

### Post by s.fox on 2009-08-31
Hi,

If you wanted to you could use a server side scripting language such as php to apply necessary formating to the word.

-Silver Fox

---

### Post by Trefethen on 2009-08-31
Hi Silver Fox, and others, thank you for your support on this topic. I am not a PHP guru nor even a hack. If you would point me to such pre-built script that would be fantastic. You guys are great.

~ Trefethen

---

### Post by stderr on 2009-08-31
Just hacked this up quickly, untested, could be vastly improved, but should give you the general idea:

```

<script type="text/javascript">
function replaceHope () {
  var b = document.getElementById('body').innerHTML;
  var reg = new RegExp('([\s])(hope)([\s\.])', 'ig');
  b.replace(reg,'$1<u>$2</u>$3');
}
</script>

```

You could combine this with CSS, so you add a CSS class to the selection, etc. Additionally, you could pull the string to find out of the regexp and pass it as a function parameter. Etc. 

You could do this server-side with PHP, Perl, ...

Lots of options! :P

---

### Post by Trefethen on 2009-08-31
> **stderr said:**
> Just hacked this up quickly, untested, could be vastly improved, but should give you the general idea:

```

<script type="text/javascript">
function replaceHope () {
  var b = document.getElementById('body').innerHTML;
  var reg = new RegExp('([\s])(hope)([\s\.])', 'ig');
  b.replace(reg,'$1<u>$2</u>$3');
}
</script>

```You could combine this with CSS, so you add a CSS class to the selection, etc. Additionally, you could pull the string to find out of the regexp and pass it as a function parameter. Etc. 

You could do this server-side with PHP, Perl, ...

Lots of options! :P

Stddr, thank you for putting this together, it looks pretty simple. However I have some questions about where to place the script and how to execute the function of it all.

Do I simply place in a new html doc then save it to the server. Once there each page will be treated with the function?

Also, what is the "selection" that I should add CSS to?

Thanks again for hacking this up. What seems simple to you is completely foreign to me.

J o h n   T r e f e t h e n
[www.TrefethenStudios.com]("http://www.TrefethenStudios.com")

---

### Post by stderr on 2009-09-12
Sorry for the delay.

You can stick that code at the top of a HTML page. It normally goes in the HEAD section as opposed to BODY, but that distinction is optional.

```

<html>
  <head>
    <script ... >...</script>
  </head>
  <body>
  </body>
</html>

```

To use it, you would call the function from within the script tags.

```

<script type="text/javascript">

// Javascript Function Definition
function replaceHope () {
  var b = document.getElementById('body').innerHTML;
  var reg = new RegExp('([\s])(hope)([\s\.])', 'ig');
  b.replace(reg,'$1<u>$2</u>$3');
}

// Javascript Function Call
replaceHope();

</script>

```

That should replace all instances of 'hope' between the <body> </body> tags.

With regard to CSS, I was simply giving that as an example of a more professional solution. So you could create a CSS class (also in the <head> section):

```

<style type="text/css">
  .highlight { font-style: bolder; font-color: red; }
</style>

```

and use javascript to add that class to the bits of text the regular expression finds. It would help to use a Javascript framework such as JQuery, then you could use the addClass() method, but all this requires more changes to the javascript I've given you for little practical benefit. Depends how much you want to learn :)

edit: Also, it's worth noting that there may be a slight delay after the page loads before the bits of text are replaced, because Javascript is a client-side language. The clients have to process the javascript code and update the page. It's worth considering that *some* people may have javascript disabled anyway (not many though, as almost every webpage uses javascript these days). A neater solution is to use a server-side language. 

You'd do something like put the text you want in the page (between the BODY tags) in a plain text file, and write a PHP/Perl/... script to compose the HTML page. It would (amongst other things) have to read the relevant text file into a string, replace the text you want in the string (similar to the javascript code), and craft the HTML page. That way, the client will receive the HTML page with highlighting already in place.

---

### Post by Trefethen on 2009-09-22
> **A neater solution is to use a server-side language. **
You'd do something like put the text you want in the page (between the BODY tags) in a plain text file, and write a PHP/Perl/... script to compose the HTML page. It would (amongst other things) have to read the relevant text file into a string, replace the text you want in the string (similar to the javascript code), and craft the HTML page. That way, the client will receive the HTML page with highlighting already in place.

I like the sound of the "neater" solution as it would allow me to use the Automator application that I am currently using to pull the entire text thread. It would also allow me to upload different instances of this idea, for other words like fear, lust, loss, etc.

Any chance you'd be able to help me prep that "neater" solution?

---

