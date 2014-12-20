# [Pylint](http://www.pylint.org/) Configuration for [Web2Py](http://web2py.com/)  
### My Personal Pylint-Web2Py Configuration settings.

### Prerequisite 
  - Follow these [instructions](http://www.pylint.org/#install) for pylint installation
  - Download [Web2Py](http://web2py.com/init/default/download) 

You can use this configuration file or follow these steps to create your own the configuration file. 
#### Steps 
   * <b> Generate Configuration File </b> <br/>

       ``` 
       $ pylint --generate-rcfile > ~/pylint_web2py.rc #rcfile_path
       ```
   * <b> Running RC file as argument </b>

       ```
       $ pylint --rcfile=~/pylint_web2py.rc applications/welcome/default.py
       ```
   * <p> After running above command ,
        You'll see some error messages and statistic information about default.py </p>
   * <b> Open RC File using editor (gedit/geany/vim/emacs) </b>

       ```
       $ emacs ~/pylint_web2py.rc
       ```
   * <b> Set Output-format </b>
    *   Output format can set to text, html, colorized, parseable or msvc (visual Studio).

	    ```
                output-format=colorized
		```
    *   It will display messages in different colors as
        *   <b> Errors messages </b> in <b> red color</b>.
        *   <b> Refactor messages </b> in <b> light purple</b>.
        *   <b> Warnings messages </b> in <b> blue color </b>.
   *   <b> Display reports </b>
    * Pylint shows statistical reports for errors/warnings/files etc. It also displays global evalution of your code. You can set it to yes or no. by default it is set to yes. If you want only messages then set it to no.

	    ```
                reports=no
		```
   * <b> Adding good-names </b>
    * Pylint always accepts variable names which are defined in adding good-names.
    * <b> For eg: I've GET, POST as function name</b>.<b>Pylint </b> gives me <b> invalid function name </b> error for these functions.  I've added them in good-names to accept it as good names

	    ```
             good-names=i,j,k,ex,Run,_,POST,GET
	    ```
   * <b> Solving Undefined variable ERROR for Web2Py</b>
    * I often get Undefined variable error for the variable like db,auth,crud,service etc. These are available as a part of Web2Py API But Pylint is unable to resolve it.
    * We can avoid these kind of errors using <b> additional-builtins </b>. Pylint assumes that names define under the <b>addition-builtins</b> are already definded

	    ```
            additional-builtins=db,auth,request,response,session...
		```
    * <b>Note:</b> I've mentioned all variables (which are available under <b> Web2py API </b>) inside the <b> additional-builtins </b>. You'll have to copy these variables 

   *  <b> Solving Import module ERROR for Web2Py </b>
    * If you've modules inside modules folder then run: </b>.

       ```
           $ pylint pylint --rcfile=~/pylint_web2py.rc ~/web2py_2.9/applications/welcome/scripts/asdf.py
       ``` 
    * You might get the <b> import module error
           *  <b> Unable to import 'gluon.tools' (import-error) </b>
           *  <b> Unable to import 'applications.welcome.modules.welcomeutils' (import-error) </b>
    * Pylint gives these errors because it is unable to find these modules. The <b> Web2py </b> stores all modules files inside <b> application/app_name/modules/all_module_files </b> 
    * The <b> init-hook </b> is used to mention base path of <b> Web2Py directory </b>.

       ```
        init-hook='import sys; sys.path.append("/home/prasad/web2py_2.9/");'
       ```

    * <b>Note: Don't forget to mention your web2py directory path </b>

Now You're ready to use pylint for web2py framework. You just need to specify the path of file or directory.

####Bugs
Feel free to report bug if you find any.

#######Follow [@rootpy](https://twitter.com/rootpy)
