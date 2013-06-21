jquery.gasp
===========

Do jquery processing with a little breathing room


Have you ever done something like...
<pre>$("td").someBigNastyPlugin();</pre>
...and it was just too much processing for your browser? (I'm looking at you, IE)

It would be nice if your browser had a little bit of time to catch its breath while it's trying to do all that processing.

jQuery.gasp to the rescue!

Include my gasp plug-in, and replace that code above with the following, and you'll have a happy browser.
<pre>$("td").gasp(function(){
  $(this).someBigNastyPlugin();
});</pre>

Essentially, it's like jquery's <em>.each</em> function, but it puts a setTimeout around each one, and chains them together, one after the other. If you saw <a href="http://wilsonhut.wordpress.com/2013/05/30/jquery-deferred-ified-window-settimeout/" title="jQuery Deferred-ified window.setTimeout">my whereas plug-in</a>, this will make more sense.

Now this is asyncronous, but it returns a promise, so you have to treat it accordingly:

<pre>
$("td").gasp(function(){
  $(this).someBigNastyPlugin();
})
.done(function(){
  console.log("This will run when it's complete");
});
console.log("This will run before the gasping is finished");
</pre>

The code includes the jquery.whereas code. Just seemed easier (for you) that way.
