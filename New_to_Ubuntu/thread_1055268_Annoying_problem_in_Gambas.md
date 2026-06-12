---
title: "Annoying problem in Gambas"
date: 2009-01-30
forum: New to Ubuntu
---

### Post by sag on 2009-01-30
Hi all,
I've installed Gambas on my laptop (Ubunto 8.10, Dual core 2GHz Intel, 4G RAM).
I am not a programmer, but I would like to be able to make some simple educational apps for my grandson, and I thought Gambas would be the ideal tool to do this.
I want to display text in a text box when a button is pressed, and add more text on a new line when another button is pressed. Simple, I thought, just do it as:
Button2_Click()
TextBox.Text = TextBox.Text & chr(10) & "More text"

But no, I get the text all on one line, with a funny square character in the place where the line break should be. I've tried all different combinations of Chr(10), Chr$(10) (dont know the difference), Chr(13), Chr$(13), \r and \n, both on the end of the first line, and the beginning of the second line.
I'm sure there is a simple way of doing this, but I cant figure it out.
Please help!
sag

---

### Post by SteveDee on 2009-01-30
> **sag said:**
> Hi all,
I've installed Gambas on my laptop (Ubunto 8.10, Dual core 2GHz Intel, 4G RAM).
I am not a programmer, but I would like to be able to make some simple educational apps for my grandson, and I thought Gambas would be the ideal tool to do this.
I want to display text in a text box when a button is pressed, and add more text on a new line when another button is pressed. Simple, I thought, just do it as:
Button2_Click()
TextBox.Text = TextBox.Text & chr(10) & "More text"

But no, I get the text all on one line, with a funny square character in the place where the line break should be. I've tried all different combinations of Chr(10), Chr$(10) (dont know the difference), Chr(13), Chr$(13), \r and \n, both on the end of the first line, and the beginning of the second line.
I'm sure there is a simple way of doing this, but I cant figure it out.
Please help!
sag

You need to use a Text Area control.

Then code:-
 TextArea1.Text = "Line 1" & Chr(10) & "Line 2"

---

### Post by sag on 2009-01-30
Hi Steve,
Thanks for that. Not sure of the distinction between a text Box & a text Area, but that works a treat now!
sag

---

### Post by SteveDee on 2009-01-31
> **sag said:**
> Hi Steve,
Thanks for that. Not sure of the distinction between a text Box & a text Area, but that works a treat now!
sag

The TextBox is a single line text edit control, while TextArea is a multiline text edit control.

Take a look at this link which includes details on the gb.qt classes:-
[http://gambasdoc.org/help/comp/gb.qt](http://gambasdoc.org/help/comp/gb.qt)

I think Gambas is a great programming language choice.

---

