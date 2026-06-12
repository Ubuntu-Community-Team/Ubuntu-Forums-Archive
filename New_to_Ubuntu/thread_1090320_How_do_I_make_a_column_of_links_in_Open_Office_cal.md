---
title: "How do I make a column of links in Open Office calc?"
date: 2009-03-08
forum: New to Ubuntu
---

### Post by occams_beard on 2009-03-08
In Open Office calc,  I have a column of 100s of URLs.  I'm trying to get these to be automatically linked so that I can just click on them to open a browser.  However, they're just plain text.

Is there a way to turn on automatic link recognition, or something like that?

The best I can do is using the HYPERLINK function to an adjacent column and then fill down, but then I end up using twice the cells that I need.

Anyone know? This is driving me crazy.

---

### Post by Rhubarb on 2009-03-08
Are you running openoffice 3 or 2.4 there?

I've got openoffice 3, and just typed in a URL into one of the cells, and it works fine for me.

---

### Post by occams_beard on 2009-03-08
Using Open Office 2.4.

Yes, if I type one in manually it turns into a link just fine... Problem is that I'm pasting in 100s at a time and they do not automatically turn into links. 

There's no way I could type them all in manually.

---

### Post by Rhubarb on 2009-03-09
After some reading online, this is indeed quite possible to achieve using a macro.

I've copied some sample code, refer to section 5.18.5. from the "English Macro Document" found here [http://www.pitonyak.org/oo.php](http://www.pitonyak.org/oo.php)

Then I've added a bit to it, to allow for processing of multiple rows in one column.

Please refer to "3.1. My first macro: “Hello World”" from the "English Macro Document" found here [http://www.pitonyak.org/oo.php](http://www.pitonyak.org/oo.php) for instructions about how to go about entering in your first macro, and how to run it.

Here is the source code for the macro that'll convert a column of URLs into real URLs with hyperlinks in a Calc Spreadsheet:-
Please note, that you'll need to enter in the correct values for startRow, currentColumn, and endRow.
- So the macro knows where the column of URLs lie so it can process them.

```
REM  *****  BASIC  *****

Sub InsertURLIntoColumn
  Dim oText   'Text object for the current object
  Dim oField  'Field to insert
  Dim oCell   'Get a specific cell
  Dim currentRow As Integer, currentColumn As Integer, startRow As Integer, endRow As Integer

  Rem Please enter in the startRow, the currentColumn, and the endRow.
  Rem This example will process the column from cell B4 to cell B8.
  startRow = 4
  currentColumn = 2
  endRow = 8
  
  Rem as we count from zero, I'll take 1 unit from currentRow, currentColumn, and endRow
  startRow = startRow - 1
  currentColumn = currentColumn - 1
  endRow = endRow - 1
  
  For currentRow = startRow To endRow
  
	  oCell = ThisComponent.Sheets(0).GetCellByPosition(currentColumn,currentRow)
	
	  REM Create a URL Text field
	  oField = ThisComponent.createInstance("com.sun.star.text.TextField.URL")
	
	  REM This is the actual text that is displayed for the URL
	  REM This could just as easily be
	  REM oField.Representation = "My Secret Text"
	  oField.Representation = oCell.getString()
	  
	  REM The URL property is just a text string of the URL itself.
	  oField.URL = ConvertToURL(oCell.getString())
	  
	  REM The text field is added as text content into the cell.
	  REM If you do not now set the string to zero, then the existing
	  REM text will remain and the new URL text field will be appended
	  REM to the end.
	  oCell.setString("")
	  oText = oCell.getText()
	  oText.insertTextContent(oText.createTextCursor(), oField, False)
  
  Next
  
End Sub
```

I've also learned a little bit about OOo Basic from this fun exercise too :)
- Rhubarb

---

### Post by occams_beard on 2009-03-10
Awesome! Thanks!!! I've been banging my head against this for days.

---

### Post by triptonemeister on 2012-02-22
Good, but it's slower than hell, if you run it on big data set... Is anybody have an idea to how to improve performance? Something like batched refresh of the ui, if it is possible? Or anything like that... Thanks!

---

### Post by sffvba[e0rt on 2012-02-22
*Old thread **closed**.*

> **triptonemeister said:**
> Good, but it's slower than hell, if you run it on big data set... Is anybody have an idea to how to improve performance? Something like batched refresh of the ui, if it is possible? Or anything like that... Thanks!

Would suggest starting a new thread and adding as much relevant information as possible.


404

---

