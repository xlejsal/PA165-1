## Seminar 07 Tasks

In this seminar, we will use several steps checked out from the GitHub repository.
Each step is marked by a git tag. A git tag is a pointer to a specific commit, 
while a git branch is a pointer to the last commit in a series of commits. 
In each step, we will reset the content of the working directory to the state
marked by each tag. You can see the final solution in the branch [seminar07](https://github.com/fi-muni/PA165/tree/seminar07/webapp-plain).


**Task 01** In a new folder, checkout the tag seminar07_step1 from https://github.com/fi-muni/PA165. 
Open the project webapp-plain. Run the application and view it in your browser at [http://localhost:8080/webapp-plain/](http://localhost:8080/webapp-plain/).
```
mkdir seminar07
cd seminar07
git clone -b seminar07_step1 https://github.com/fi-muni/PA165
cd PA165/webapp-plain
mvn tomcat7:run
```

**Task 02** Open the project in your favorite IDE. Inspect all the files in the application and decide what is their purpose.
The application contains:
 * a ServletContextListener in the class MyStartListener
 * a Filter in the class CharacterEncodingFilter
 * a Servlet in the class HomeServlet
 * a localization ResourceBundle in the files Texts*.properties
 * some JSP pages in the *.jsp files
 * a cascading stylesheet in the file style.css
 * an image in the file favicon.ico used as an icon in browser tabs and bookmarks
 * two custom JSP tags in the *.tag files
 * the configuration file logback.xml for the Logback logging framework
 * libraries for JSTL (JSP Standard Tag Library), SLF4J and Logback 

Change the setting of your browser accepted language subsequently to Czech and English
and check whether everything in the application is properly localized in both languages.

**Task 03** Add a logging statement to CharacterEncodingFilter to log the called URL on the "trace" level.
Modify the logback.xml file to see the log events. Re-run the application and check the log.

**Task 04** Click on the "to Prague" link in the navigation menu. Go back and click on the direct link to praha.jsp on the home page.
Explain the difference of the output. Move the file praha.jsp to the WEB-INF/hidden-jsps/
folder so that it cannot be called directly, and modify PrahaServlet class to forward
to the new location of the JSP.

**Task 05**  Make all changes needed for the third item in the navigation menu to work. It means - create a servlet, 
a JSP page, localized texts in the Texts*.properties files 

**Task 06** Modify the page template in the file pagetemplate.tag so that every page has a footer
which says `&copy; Masaryk University`. Modify the CSS stylesheet in the file style.css so that
the footer has light blue background color. (You may need to force cache refresh in your browser to see the CSS change.)

**Task 07** Create a new filter mapped to every request that adds a request attribute with key "currentyear"
and a string value with the current year number (i.e. 2015). Modify the page template pagetemplate.tag
so that the page footer copyright message includes the attribute value.

(Hints: [ServletRequest.setAttribute(String,Object)](http://docs.oracle.com/javaee/6/api/javax/servlet/ServletRequest.html#setAttribute(java.lang.String, java.lang.Object))
[SimpleDateFormat(String,Locale)](http://docs.oracle.com/javase/8/docs/api/java/text/SimpleDateFormat.html#SimpleDateFormat-java.lang.String-java.util.Locale-)
[ServletRequest.getLocale()](http://docs.oracle.com/javaee/6/api/javax/servlet/ServletRequest.html#getLocale()) )


**Task 08** Check out tag seminar07_step2 from the repository, forcing the reset of files (your changes will be deleted):
```
git checkout -f seminar07_step2
```
New files will appear:
* a servlet class PharmacyServlet
* a JSP page pharmacy.jsp 
Run the updated application and add some data using the form. Inspect how the form works.

**Task 09**
Add a third property *vendor* to drugs, i.e. add it to the javabean, the form and to the table.
 
**Task 10** Let's try some attack. Enter the value `<script>location.href='http://seznam.cz/';</script>` for the name 
of the drug and submit the form. This was a successful Cross Site Scripting (XSS) attack. Prevent the attack.

**Task 11** Check out tag seminar07_step3 from the repository:
```
git checkout -f seminar07_step3
```
There is a new class ProtectFilter. Run the application and visit the page with the form again. Provide the correct username and password. 