---
title: "Terminal wraps text incorrectly when using hidden characters"
date: 2009-10-26
forum: New to Ubuntu
---

### Post by LawnMowerMan on 2009-10-26
Hi everyone, new forum member here. I have a background in Unix and I can't believe its taken me this long to finally install the current (9.0.4) Ubuntu to a VM.

Anyway, after getting Ubuntu up and running with much less fuss and time than I had expected, I set myself a task of 'converting' an old non-GUI Unix C program to run in my shiny new environment. To be honest, there wasn't much converting to be done before much of the program was working.

The original program was structured to suit the old HP-UX non-ansi compliant compiler. Some parts of this program outputs a list to the terminal in a table format, with column headings that are underlined. I also use bold text in some of the output. To acheive this I use escape characters, such as [COLOR=#000000]"\033[4m" for underlining.

My minor niggle is that the termial window does not seem to ignore hidden escape characters when determining when to wrap text in the window. Therefore, when I use underline or bold in a heading the text always wraps in the wrong place.

Is there a setting in Terminal that tells it to ignore escape characters, or should I open a bug report?
[/COLOR]

---

