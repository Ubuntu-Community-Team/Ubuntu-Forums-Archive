---
title: "ASP and Firefox issues"
date: 2009-09-04
forum: New to Ubuntu
---

### Post by mistypotato on 2009-09-04
Hi,

I am having issues with ASP pages working properly under Firefox.

Are there any known issues?

My understanding is that ASP code must be very well written to work in Forfox (meaning it must comply to the strict standards) whereas Internet Explorer is "ASP savvy" and is therefor more forgiving of sloppy asp coding....which would mean the programmer is writing for IE and basically not checking to be sure it works with Firefox or not.

So, when an asp page works in IE, but does not work in Firefox, the programmer needs to be contacted?

Is any of this correct or can you enlighten me a bit please?

thx

---

### Post by zerhacke on 2009-09-04
What do you mean by "issues with ASP pages working properly"?

Each server is different, and they might not have their MIME types set up right.

---

### Post by mistypotato on 2009-09-04
Basically errors and pages not functioning in terms of javascripts.
It has to do with Firefox.

**Keep in mind the pages work perfectly in Internet Explorer.**

Error: SearchMenuLast is not defined
Source File: [http://123.456.78.90/dt_wb1/or_sch_1.asp](http://123.456.78.90/dt_wb1/or_sch_1.asp)
Line: 91



	
**Here is the source from the page..........	**
	
<!DOCTYPE HTML PUBLIC "-//W3C//DTD HTML 4.0 Transitional//EN">
	
	
<html>
<head>
<title>Start a New Search</title>
<link rel="STYLESHEET" type="TEXT/CSS" href="core_style.css">








<STYLE type=text/css>
#window1 {position: absolute;
          visibility: visible;
}
#window2 {position: absolute;
          visibility: hidden;
}
#window3 {position: absolute;
          visibility: hidden;
}
#window4 {position: absolute;
          visibility: hidden;
}
#window5 {position: absolute;
          visibility: hidden;
}
A.tab:link { 
	color: navy; 
	font-family: Verdana, Arial, Helvetica;
	font-weight: 400;
	font-size: 12px;

}
A.tab:visited {
	color: navy; 
	font-family: Verdana, Arial, Helvetica;
	font-weight: 400;
	font-size: 12px;
}
A.tab:hover {
	color: red; 
	font-family: Verdana, Arial, Helvetica;
	font-weight: 400;
	font-size: 12px;
}
</STYLE>




<SCRIPT Language="JavaScript">
<!--



leftPos=0
if (screen) {
			leftPos = screen.width - 510
			}



var lastmenu = 'window1';
var visible = 'visible';
var hidden  = 'hidden';


function MenuTog(menu) {

  if (document.layers) { //Netscape
    SearchMenuCurrent = document.layers[menu];
    SearchMenuLast = document.layers[lastmenu];


  } else if (document.all) { //IE
    SearchMenuCurrent = document.all(menu).style;
    SearchMenuLast = document.all(lastmenu).style;
	

  }

  SearchMenuLast.visibility    = 'hidden';
  SearchMenuCurrent.visibility = 'visible';
  lastmenu = menu;

}



  
//-->
</SCRIPT>










<SCRIPT LANGUAGE="JAVASCRIPT">
function Trim(a_string)
{
	while (a_string.charAt(0) == " ")
		a_string = a_string.slice(1)

	while (a_string.charAt(a_string.length - 1) == " ")
		a_string = a_string.slice(0, a_string.length - 2)

	return a_string
}

function Select(SelectObj,Selection)
{
	var i=0
	while (i < SelectObj.length)
	{
		if (SelectObj.options[i].value == Selection)
			SelectObj.options[i].selected = 1
		i ++
	}
}

function ValidateAndSubmit(theForm)
{
	theForm.search_entry.value = Trim(theForm.search_entry.value)
	if (theForm.search_entry.value == "")
	{
		alert("Please enter the Search entry.")
		theForm.search_entry.focus()
		return false
	}
	

	if (theForm.search_by.value=="DocType") 
	{
		if (theForm.FromDate.value != "" &&
			 theForm.ToDate.value != "")
		{
			theForm.submit()
		}
	}

	else
		if (theForm.search_by.value=="Name")
		{
			if ((theForm.FromDate.value != "" &&
				 theForm.ToDate.value != "" ) ||
				 (theForm.FromDate.value == "" &&
				 theForm.ToDate.value == "" ))
				theForm.submit()
			else	
			{
				alert("Please complete the date range input.")
				theForm.FromDate.focus()
				return false
			}
		}
	else
		theForm.submit()
}





function ValidateAndSubmitProp(theForm)
{
	theForm.search_entry.value = Trim(theForm.search_entry.value)
	if (theForm.search_entry.value == "")
	{
		alert("Please enter the Search entry.")
		theForm.search_entry.focus()
		return false
	}


	
	if (theForm.search_by.options[theForm.search_by.selectedIndex].value=="PropertyName")
	{
				leftPos=0
					searchentry = theForm.search_entry.value
					page_size = theForm.PageSize.options[theForm.PageSize.selectedIndex].value
					rec_set_size = theForm.RecSetSize.options[theForm.RecSetSize.selectedIndex].value
					while(searchentry.indexOf(' ') > -1)
					{
						
						before_space = searchentry.substring(0,searchentry.indexOf(' '))
						after_space = searchentry.substring(searchentry.indexOf(' ') + 1, searchentry.length)
						searchentry = before_space + "%20" + after_space
					}
					
				hlink="prop_panel.asp?search_by=PropertyName&refresh=no&PageSize=" + page_size + "&RecSetSize=" + rec_set_size + "&search_entry=" + searchentry
					if (screen) 
					{
						leftPos = screen.width - 510
					}
			
				newWindow = window.open(''+hlink+'', 'newWin', 'scrollbars=1,status=1,width=500,height=400,resizable=1, left='+leftPos+' ')
					
				return false
		
	}
	
	
	
	
	
	if (theForm.search_by.options[theForm.search_by.selectedIndex].value=="PlatBook/Page")
	{
				leftPos=0
				page_size = theForm.PageSize.options[theForm.PageSize.selectedIndex].value
				rec_set_size = theForm.RecSetSize.options[theForm.RecSetSize.selectedIndex].value
				hlink="prop_panel.asp?search_by=PlatBook/Page&refresh=no&PageSize=" + page_size + "&RecSetSize=" + rec_set_size + "&search_entry=" + theForm.search_entry.value
					if (screen) 
					{
						leftPos = screen.width - 510
					}
			
				newWindow = window.open(''+hlink+'', 'newWin', 'scrollbars=1,status=1,width=500,height=400,resizable=1, left='+leftPos+' ')
				
				return false
		
	}
	
	
	
	
	
	if (theForm.search_by.options[theForm.search_by.selectedIndex].value=="Section/Township/Range")
	{
				leftPos=0
				page_size = theForm.PageSize.options[theForm.PageSize.selectedIndex].value
				rec_set_size = theForm.RecSetSize.options[theForm.RecSetSize.selectedIndex].value
				hlink="prop_panel.asp?search_by=Section/Township/Range&refresh=no&PageSize=" + page_size + "&RecSetSize=" + rec_set_size + "&search_entry=" + theForm.search_entry.value
					if (screen) 
					{
						leftPos = screen.width - 510
					}
			
				newWindow = window.open(''+hlink+'', 'newWin', 'scrollbars=1,status=1,width=500,height=400,resizable=1, left='+leftPos+' ')
					
				return false
		
	}
	
	
	
	if (theForm.search_by.value=="Name")
	{
			if ((theForm.FromDate.value != "" &&
				 theForm.ToDate.value != "" ) ||
				 (theForm.FromDate.value == "" &&
				 theForm.ToDate.value == "" ))
				theForm.submit()
			else	
			{
				alert("Please complete the date range input.")
				theForm.FromDate.focus()
				return false
			}
		
	}
	else
	{
		theForm.submit()
	}
}






</SCRIPT>








</head>
<body marginwidth="0" marginheight="0" topmargin="0" leftmargin="0" rightmargin="0" link="#800000" vlink="#800000" >









<table border="0" width="100%" cellspacing="0" cellspacing="0">
	<tr>
		<td width="100%" align="center" valign="center" bgcolor="#336699" autosize="true">&nbsp;&nbsp;&nbsp;<font face="Verdana, Arial, Helvetica" size="4" color="white">Clerk of the Courts</td></font>
    </tr>
</table> 
<table width="100%" cellspacing="0" cellpadding="0" border="0">

	<tr>
	  <td align="right" height="21" bgcolor=#EEEECC>&nbsp;
				   		<a class="heading" href="default.asp" >Home</a>&nbsp;|&nbsp;
				   		<a class="heading" href="or_sch_1.asp" >New Search</a>&nbsp; 
						
		</td>
	</tr>
</table>
<br>
		

<br>

<div align="center">
<table border="0" width="100%" cellspacing="3" cellpadding="0" >
	<tr>
		<td class="title" width="100%" align="center" valign="center" colspan="3">DEEDS</td>
	</tr>
	<tr>
		<td class="verifytext" width="100%" align="center" valign="center" colspan="3">
				
					&nbsp;Verified as of 8/31/2009&nbsp;

				
		</td>
	</tr>
	<tr>
		<td width="100%" align="center" colspan="3">&nbsp;</td>
	</tr>
	<tr>
		<td width="100%" align="center" colspan="3"><font FACE="verdana" size="2" color="navy">Click tabs to select a search criteria:</font></td>
	</tr>  
	

</table>
</div>

<br>










<DIV id="window1">
<TABLE width=100% border=0 cellpadding=0 cellspacing=0>
	<TR>

		<TD align=center>
			<TABLE border=0 width=650 border=0 cellpadding=0 cellspacing=0>
				<TR>
			    	<TD height="30" width=17% align=center bgcolor="navy">
						<FONT face=Arial size=2 color="white" ><B>Name</B></FONT></td>
					</TD>
			    	<TD height="30" width=3% bgcolor="white" align="center">&nbsp;&nbsp;</TD>
			    	<TD height="30" width=17% align=center bgcolor="#dcdcdc">

			     		<A href="#" onclick="javascript: MenuTog('window2'); return false;">
			      		<FONT face=Arial size=2 color="navy">Tax Number</FONT></A>
					</TD>
			    	<TD height="30" width=3% bgcolor="white" align="center">&nbsp;&nbsp;</TD>
					
					<TD height="30" width=17% align=center bgcolor="#dcdcdc">
			      		<A href="#" onclick="javascript: MenuTog('window3'); return false;">
			      		<FONT face=Arial size=2 color="navy">Lands Available</FONT></A>
					</TD>

					<TD height="30" width=3% bgcolor="white" align="center">&nbsp;&nbsp;</TD>
					
			    	<TD height="30" width=17% align=center bgcolor="#dcdcdc">
			      		<A href="#" onclick="javascript: MenuTog('window4'); return false;">
			      		<FONT face=Arial size=2 color="navy">Parcel Number</FONT></A>
					</TD>
			    	<TD height="30" width=3% bgcolor="white" align="center">&nbsp;&nbsp;</TD>
			    	<TD height="30" width=17% align="center" bgcolor="#dcdcdc">
			      		<A href="#" onclick="javascript: MenuTog('window5'); return false;">

			      		<FONT face=Arial size=2 color="navy">Sale Date</FONT></A>
					</TD>
			  	</TR>
				<tr><td colspan="9" bgcolor="navy"><img src="images/spacer.gif" alt="" height="3"></td></tr>
				
				<TR>
					<TD colspan="9" align="center" bgcolor="white">
						<table width="100%" border="0" cellpadding="0" cellspacing="0" bordercolor="navy">
							<TR>

								<TD align="center" bgcolor="#ffffcc" >
								<FORM name="formSearch1" method="post" action="new_sch.asp">
									
									
											
												
										<br>
											
											<FONT face=Arial size=2 color="navy"><strong>Select Type of Name Search</strong></font>
											
											<br>
											<br>
						    				<select name="search_by">
												<option value="Any Party">Any Party&nbsp;&nbsp;(both Applicants and Owners)</option>

												<option value="Applicant">Deed Applicant&nbsp;&nbsp;</option>
												<option value="Owner">Deed Owner&nbsp;&nbsp;</option>
												
											</select>
											
		
											<br>
											<br>
											
										
										
										
										
										
											<hr width="80%">	
											
											<FONT face=Arial size="2" color="navy"><strong>Enter Name</strong></font>
													
											<br>

											<br>
											<input type="hidden" name="refresh" value="no">
											<FONT face=Arial size=3><INPUT name="search_entry" type="text" size="25" maxlength="30"></FONT>
													&nbsp;&nbsp;<INPUT name="button" type="button" value="&nbsp;&nbsp;&nbsp;Search&nbsp;&nbsp;&nbsp;" onClick="javascript:ValidateAndSubmit(this.form)">
													&nbsp;&nbsp;&nbsp;&nbsp;<INPUT TYPE="Reset" VALUE="Clear">
													
											
											
											
											<br><br>
														<FONT face=Arial size=2 color="navy">Enter the First-Name Last-Name (e.g., Al Smith) or the Company name (e.g., Big Utility)</FONT>
											<br>	
														<FONT face=Arial size=2 color="navy">Use no commas between the First-Name and Last-Name.</FONT>

											<br><br>
														
											
											
											<hr width="80%">
										
										
												<FONT face=Arial size="2" color="navy"><strong>Search Options</strong></font>
												<br>	
												<br>
									

											
												<FONT face=Arial size="2" color="navy">
												<select name="RecSetSize">
													<option value="100"   selected  >Show first 100 records</option>

													<option value="500"   >Show first 500 records</option>
													<option value="1000"  >Show first 1000 records</option>
													<option value="2000"  >Show first 2000 records</option>
												</select>
												<br>
												Display 
												<select name="PageSize">
													<option value="20"   selected  >20
													<option value="30"   >30
													<option value="50"   >50
													<option value="100"  >100
												</select>&nbsp;Records Per Page
												
												
												<br>

												
												<INPUT TYPE="checkbox" NAME="ShowProperties" VALUE="YES"  >Check Here to Save Search Options
												
												
												</FONT>
											
											<br>
										
								
									</FORM>
								</td>
							</tr>
							<tr>
								<td align="center">
									<br>	
									<div class="copyright">

										&nbsp;Copyright &copy; 2009 by <u>Systems Corporation.</u> All rights reserved.

									<br><br><br>
									</div>
								
								
								</td>
							
							</tr>
							
						</table> 
						
						
							
					</TD>

				</TR>
			</TABLE>
		</TD>
	</TR>
</TABLE>	
			
 		

</DIV>




<DIV id="window2">

<TABLE width=100% border=0 cellpadding=0 cellspacing=0>

	<TR>
		<TD align=center>

			<TABLE width=650 border=0 cellpadding=0 cellspacing=0>
				<TR>
    				<TD height="30" width=17% align=center bgcolor="#dcdcdc">
     	 				<A href="#" onclick="javascript: MenuTog('window1'); return false;">
      					<FONT face=Arial size=2 color="navy">Name</FONT></A>
					</TD>

    				<TD height="30" width=3% bgcolor="white" align="center">&nbsp;&nbsp;</TD>
    				<TD height="30" width=17% align=center bgcolor=navy>
						<FONT face=Arial size=2 color=white><B>Tax Number</B></FONT>
					</TD>
    				<TD height="30" width=3% bgcolor="white" align="center">&nbsp;&nbsp;</TD>
					
					<TD height="30" width=17% align=center bgcolor="#dcdcdc">
			      		<A href="#" onclick="javascript: MenuTog('window3'); return false;">
			      		<FONT face=Arial size=2 color="navy">Lands Available</FONT></A>

					</TD>
					<TD height="30" width=3% bgcolor="white" align="center">&nbsp;&nbsp;</TD>
					
    				<TD height="30" width=17% align=center bgcolor="#dcdcdc">
      					<A href="#" onclick="javascript: MenuTog('window4'); return false;">
      					<FONT face=Arial size=2 color="navy">Parcel Number</FONT></A>
					</TD>
    				<TD height="30" width=3% bgcolor="white" align="center">&nbsp;&nbsp;</TD>
    				<TD height="30" width=17% align=center bgcolor="#dcdcdc">

      					<A href="#" onclick="javascript: MenuTog('window5'); return false;">
      					<FONT face=Arial size=2 color="navy">Sale Date</FONT></A>
					</TD>
				</TR>
				<tr><td colspan="9" bgcolor="navy"><img src="images/spacer.gif" alt="" height="3"></td></tr>
				<TR>
					<TD colspan="9" align=center bgcolor=white>
							
						<table width="100%" border="0" cellpadding="0" cellspacing="0" bordercolor="navy">

							<TR>
								<TD colspan=7 align="center" bgcolor="#ffffcc">
									<FORM name="formSearch2" method="post" action="new_sch.asp">
									<input type="hidden" name="search_by" value="Tax Number">
									
									
									
											<br>
											<FONT face=Arial size=2 color="navy"><strong>Enter Number</strong></font>
											<br>
											<br>

										
						    				<FONT face=Arial size=3><INPUT name="search_entry" type="text" size="20" maxlength="30"></FONT>
											&nbsp;&nbsp;<INPUT name="button" type="button" value="&nbsp;&nbsp;&nbsp;Search&nbsp;&nbsp;&nbsp;" onClick="javascript:ValidateAndSubmit(this.form)">
											&nbsp;&nbsp;&nbsp;&nbsp;<INPUT TYPE="Reset" VALUE="Clear">
										
										
										<br><br>
										
											<FONT face=Arial size=2 color="navy">Numbers only, without a dash (e.g., 123456789)</FONT>
											
											
										
										<br><br>
									
											
											
											
				
										<hr width="80%">
										
										
												<FONT face=Arial size="2" color="navy"><strong>Search Options</strong></font>

												<br>	
												<br>
									

											
												<FONT face=Arial size="2" color="navy">
												<select name="RecSetSize">
													<option value="100"   selected  >Show first 100 records</option>
													<option value="500"   >Show first 500 records</option>
													<option value="1000"  >Show first 1000 records</option>
													<option value="2000"  >Show first 2000 records</option>

												</select>
												<br>
												Display 
												<select name="PageSize">
													<option value="20"   selected  >20
													<option value="30"   >30
													<option value="50"   >50
													<option value="100"  >100
												</select>&nbsp;Records Per Page
												
												
												<br>
												
												<INPUT TYPE="checkbox" NAME="ShowProperties" VALUE="YES"  >Check Here to Save Search Options
												
												
												</FONT>

											
											<br>
										
									</FORM>
								</td>
							</tr>
							<tr>
								<td align="center">
									<br>	
									<div class="copyright">
										&nbsp;Copyright &copy; 2009 by <u>Systems Corporation.</u> All rights reserved.

									<br><br><br>

									</div>
								
								
								</td>
							
							</tr>
							
						</table> 
				
					</TD>
				</TR>
			</TABLE>
			
		</TD>
	</TR>

</TABLE>		
</DIV>




<DIV id="window3">

<TABLE width=100% border=0 cellpadding=0 cellspacing=0>
	<TR>
		<TD align=center>
			<TABLE width=650 border=0 cellpadding=0 cellspacing=0>
				<TR>

    				<TD height="30" width=17% align=center bgcolor="#dcdcdc">
      					<A href="#" onclick="javascript: MenuTog('window1'); return false;">
      					<FONT face=Arial size=2 color="navy" >Name</FONT></A>
					</TD>
    				<TD height="30" width=3% bgcolor="white" align="center">&nbsp;&nbsp;</TD>
    				<TD height="30" width=17% align=center bgcolor="#dcdcdc">
      					<A href="#" onclick="javascript: MenuTog('window2'); return false;">
      					<FONT face=Arial size=2 color="navy" >Tax Number</FONT></A>

					</TD>
    				<TD height="30" width=3% bgcolor="white" align="center">&nbsp;&nbsp;</TD>
					<TD height="30" width=17% align=center bgcolor=navy>
						<FONT face=Arial size=2 color=white><B> Available</B></FONT>
					</TD>
					<TD height="30" width=3% bgcolor="white" align="center">&nbsp;&nbsp;</TD>
    				<TD height="30" width=17% align=center bgcolor="#dcdcdc">
      					<A href="#" onclick="javascript: MenuTog('window4'); return false;">

      					<FONT face=Arial size=2 color="navy" >Parcel Number</FONT></A>
					</TD>
    				<TD height="30" width=3% bgcolor="white" align="center">&nbsp;&nbsp;</TD>
					<TD height="30" width=17% align=center bgcolor="#dcdcdc">
      					<A href="#" onclick="javascript: MenuTog('window5'); return false;">
      					<FONT face=Arial size=2 color="navy" >Sale Date</FONT></A>
					</TD>
				</TR>

				<tr><td colspan="9" bgcolor="navy"><img src="images/spacer.gif" alt="" height="3"></td></tr>
				<TR>
					<TD colspan="9" align=center bgcolor=white>
						<table width="100%" border="0" cellpadding="0" cellspacing="0" bordercolor="navy">
						
							<TR>
								<TD colspan=7 align="center" bgcolor="#ffffcc" >
									<FORM name="formSearch3" method="post" action="new_sch.asp">
									<input type="hidden" name="search_by" value="Available">
									
											<br>

												<FONT face=Arial size=2 color="navy"><strong>Enter Start Date</strong></font>
											<br>
											<br>
						    				<FONT face=Arial size=3>
											<INPUT name="search_entry" type="text" size="10" maxlength="10">
											</FONT>
											
											&nbsp;&nbsp;<INPUT name="button" type="button" value="&nbsp;&nbsp;&nbsp;Search&nbsp;&nbsp;&nbsp;" onClick="javascript:ValidateAndSubmit(this.form)">
											&nbsp;&nbsp;&nbsp;&nbsp;<INPUT TYPE="Reset" VALUE="Clear">

											
											<br><br>
										
						
										
												<FONT face=Arial size=2 color="navy">Use numbers only, separated by slashes.(e.g., 01/07/2000)</FONT>
												<br>
												<FONT face=Arial size=2 color="navy">*Results will have a Date on or after the date entered.</FONT>
												
											<br><br>
											
										
											<hr width="80%">	
									
						    			
												<FONT face=Arial size="2" color="navy"><strong>Search Options</strong></font>
												<br>	
												<br>

									

											
												<FONT face=Arial size="2" color="navy">
												<select name="RecSetSize">
													<option value="100"   selected  >Show first 100 records</option>
													<option value="500"   >Show first 500 records</option>
													<option value="1000"  >Show first 1000 records</option>
													<option value="2000"  >Show first 2000 records</option>
												</select>

												<br>
												Display 
												<select name="PageSize">
													<option value="20"   selected  >20
													<option value="30"   >30
													<option value="50"   >50
													<option value="100"  >100
												</select>&nbsp;Records Per Page
												
												
												<br>
												
												<INPUT TYPE="checkbox" NAME="ShowProperties" VALUE="YES"  >Check Here to Save Search Options
												
												
												</FONT>
											
											<br>

						
										
									
									
									</FORM>
									
									
								
						
								</td>
							</tr>
							<tr>
								<td align="center">
									<br>	
									<div class="copyright">
										&nbsp;Copyright &copy; 2009 by <u>Systems Corporation.</u> All rights reserved.

									<br><br><br>

									</div>
								
								
								</td>
							
							</tr>
						</table> 
						
						
							
					</TD>
				</TR>
			</TABLE>
			
		</TD>
	</TR>

</TABLE>
</DIV>






<DIV id="window4">

<TABLE width=100% border=0 cellpadding=0 cellspacing=0>
	<TR>
		<TD align=center>
			<TABLE width=650 border=0 cellpadding=0 cellspacing=0>

				<TR>
    				<TD height="30" width=17% align=center bgcolor="#dcdcdc">
      					<A href="#" onclick="javascript: MenuTog('window1'); return false;">
      					<FONT face=Arial size=2 color="navy" >Name</FONT></A>
					</TD>
    				<TD height="30" width=3% bgcolor="white" align="center">&nbsp;&nbsp;</TD>
    				<TD height="30" width=17% align=center bgcolor="#dcdcdc">
      					<A href="#" onclick="javascript: MenuTog('window2'); return false;">

      					<FONT face=Arial size=2 color="navy" >Tax Number</FONT></A>
					</TD>
    				<TD height="30" width=3% bgcolor="white" align="center">&nbsp;&nbsp;</TD>
					
					<TD height="30" width=17% align=center bgcolor="#dcdcdc">
			      		<A href="#" onclick="javascript: MenuTog('window3'); return false;">
			      		<FONT face=Arial size=2 color="navy">Lands Available</FONT></A>
					</TD>
					<TD height="30" width=3% bgcolor="white" align="center">&nbsp;&nbsp;</TD>

					
    				<TD height="30" width=17% align=center bgcolor=navy>
						<FONT face=Arial size=2 color=white><B>Parcel Number</B></FONT></TD>
    				<TD height="30" width=3% bgcolor="white" align="center">&nbsp;&nbsp;</TD>
    				<TD height="30" width=17% align=center bgcolor="#dcdcdc">
      					<A href="#" onclick="javascript: MenuTog('window5'); return false;">
      					<FONT face=Arial size=2 color="navy" >Sale Date</FONT></A>
					</TD>
				</TR>

				<tr><td colspan="9" bgcolor="navy"><img src="images/spacer.gif" alt="" height="3"></td></tr>
				<TR>
					<TD colspan="9" align=center bgcolor=white>
						<table width="100%" border="0" cellpadding="0" cellspacing="0" bordercolor="navy">
						
							<TR>
								<TD colspan=7 align="center" bgcolor="#ffffcc" >
									<FORM name="formSearch4" method="post" action="new_sch.asp">
									<input type="hidden" name="search_by" value="Parcel Number">
									
											<br>

												<FONT face=Arial size=2 color="navy"><strong>Enter Parcel Number</strong></font>
											<br>
											<br>
						    				<FONT face=Arial size=3>
											<INPUT name="search_entry" type="text" size="20" maxlength="30">
											</FONT>
											
											&nbsp;&nbsp;<INPUT name="button" type="button" value="&nbsp;&nbsp;&nbsp;Search&nbsp;&nbsp;&nbsp;" onClick="javascript:ValidateAndSubmit(this.form)">
											&nbsp;&nbsp;&nbsp;&nbsp;<INPUT TYPE="Reset" VALUE="Clear">

											
											<br><br>
										
						
										
												<FONT face=Arial size=2 color="navy">Numbers only, without a dash (e.g., 123456778889)</FONT>
												
											<br><br>
											
										
											<hr width="80%">	
									
						    			
												<FONT face=Arial size="2" color="navy"><strong>Search Options</strong></font>
												<br>	
												<br>
									

											
												<FONT face=Arial size="2" color="navy">
												<select name="RecSetSize">

													<option value="100"   selected  >Show first 100 records</option>
													<option value="500"   >Show first 500 records</option>
													<option value="1000"  >Show first 1000 records</option>
													<option value="2000"  >Show first 2000 records</option>
												</select>
												<br>
												Display 
												<select name="PageSize">

													<option value="20"   selected  >20
													<option value="30"   >30
													<option value="50"   >50
													<option value="100"  >100
												</select>&nbsp;Records Per Page
												
												
												<br>
												
												<INPUT TYPE="checkbox" NAME="ShowProperties" VALUE="YES"  >Check Here to Save Search Options
												
												
												</FONT>
											
											<br>
						
										
									
									
									</FORM>
									
									
								
						
								</td>
							</tr>

							<tr>
								<td align="center">
									<br>	
									<div class="copyright">
										&nbsp;Copyright &copy; 2009 by <u>Systems Corporation.</u> All rights reserved.

									<br><br><br>
									</div>

								
								
								</td>
							
							</tr>
						</table> 
						
						
							
					</TD>
				</TR>
			</TABLE>
			
			
		</TD>
	</TR>
</TABLE>		
</DIV>











<DIV id="window5">

<TABLE width=100% border=0 cellpadding=0 cellspacing=0>
	<TR>
		<TD align=center>

			<TABLE width=650 border=0 cellpadding=0 cellspacing=0>
				<TR>
    				<TD height="30" width=17% align=center bgcolor="#dcdcdc">
      					<A href="#" onclick="javascript: MenuTog('window1'); return false;">
      					<FONT face=Arial size=2 color="navy" >Name</FONT></A>
					</TD>
    				<TD height="30" width=3% bgcolor="white" align="center">&nbsp;&nbsp;</TD>
    				<TD height="30" width=17% align=center bgcolor="#dcdcdc">

      					<A href="#" onclick="javascript: MenuTog('window2'); return false;">
      					<FONT face=Arial size=2 color="navy" >Tax Number</FONT></A>
					</TD>
    				<TD height="30" width=3% bgcolor="white" align="center">&nbsp;&nbsp;</TD>
					
					<TD height="30" width=17% align=center bgcolor="#dcdcdc">
			      		<A href="#" onclick="javascript: MenuTog('window3'); return false;">
			      		<FONT face=Arial size=2 color="navy">Lands Available</FONT></A>
					</TD>

					<TD height="30" width=3% bgcolor="white" align="center">&nbsp;&nbsp;</TD>
					
    				<TD height="30" width=17% align=center bgcolor="#dcdcdc">
      					<A href="#" onclick="javascript: MenuTog('window4'); return false;">
      					<FONT face=Arial size=2 color="navy" >Parcel Number</FONT></A>
					</TD>
    				<TD height="30" width=3% bgcolor="white" align="center">&nbsp;&nbsp;</TD>
    				<TD height="30" width=17% align=center bgcolor=navy>
						<FONT face=Arial size=2 color=white><B>Sale Date</B></FONT>

					</TD>
				</TR>
				<tr><td colspan="9" bgcolor="navy"><img src="images/spacer.gif" alt="" height="3"></td></tr>
				<TR>
					<TD colspan="9" align=center bgcolor=white>
					
						
						<table width="100%" border="0" cellpadding="0" cellspacing="0" bordercolor="navy">
						
							<TR>
								<TD colspan=7 align="center" bgcolor="#ffffcc" >
									<FORM name="formSearch5" method="post" action="new_sch.asp">

									<input type="hidden" name="search_by" value="Date">
									<br>
										<FONT face=Arial size=2 color="navy"><strong>Enter Beginning Date</strong></font>
									<br>
									<br>
									
										
										
										
						    		<FONT face=Arial size=3>
									<INPUT name="search_entry" type="text" size="10" maxlength="10">
									</FONT>

									&nbsp;&nbsp;<INPUT name="button" type="button" value="&nbsp;&nbsp;&nbsp;Search&nbsp;&nbsp;&nbsp;" onClick="javascript:ValidateAndSubmit(this.form)">
				 					&nbsp;&nbsp;&nbsp;&nbsp;<INPUT TYPE="Reset" VALUE="Clear">
									
									<br><br>	
										
						
									<FONT face=Arial size=2 color="navy">Use numbers only, separated by slashes.(e.g., 01/07/2000) </FONT>
									
									
									<br>
									<br>
										
						
									<hr width="80%">	
									
						    			
												<FONT face=Arial size="2" color="navy"><strong>Search Options</strong></font>
												<br>	
												<br>

									

											
												<FONT face=Arial size="2" color="navy">
												<select name="RecSetSize">
													<option value="100"   selected  >Show first 100 records</option>
													<option value="500"   >Show first 500 records</option>
													<option value="1000"  >Show first 1000 records</option>
													<option value="2000"  >Show first 2000 records</option>
												</select>

												<br>
												Display 
												<select name="PageSize">
													<option value="20"   selected  >20
													<option value="30"   >30
													<option value="50"   >50
													<option value="100"  >100
												</select>&nbsp;Records Per Page
												
												
												<br>
												
												<INPUT TYPE="checkbox" NAME="ShowProperties" VALUE="YES"  >Check Here to Save Search Options
												
												
												</FONT>
											
										<br>

						
										<!-- <INPUT NAME="Search" TYPE="submit" VALUE="Search" onClick="javascript:ValidateAndSubmit(this.form)"> --> 
										
									
									</FORM>
								</td>
							</tr>
							<tr>
								<td align="center">
									<br>	
									<div class="copyright">
										&nbsp;Copyright &copy; 2009 by <u> Systems Corporation.</u> All rights reserved.

									<br><br><br>

									</div>
								
								
								</td>
							
							</tr>
							
						</table> 
						
						
						
							
					</TD>
				</TR>
			</TABLE>
			
		</TD>
	</TR>

</TABLE>	
</DIV>



<P>&nbsp;</P>
<P>&nbsp;</P>
<P>&nbsp;</P>
<P>&nbsp;</P>
<P>&nbsp;</P>
<P>&nbsp;</P>
<P>&nbsp;</P>
<P>&nbsp;</P>
<P>&nbsp;</P>
<P>&nbsp;</P>
<P>&nbsp;</P>
<P>&nbsp;</P>

<P>&nbsp;</P>
<P>&nbsp;</P>
<P>&nbsp;</P>
<P>&nbsp;</P>
<P>&nbsp;</P>
<P>&nbsp;</P>
<P>&nbsp;</P>
<P>&nbsp;</P>
<P>&nbsp;</P>
<P>&nbsp;</P>
<P>&nbsp;</P>
<P>&nbsp;</P>





		
</body>

</html>

---

