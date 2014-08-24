# Nginx config base

This directory holds an nginx boilerplate config. Drop it in your nginx config
folder and adds website-specific config and you're good to go.

# Location rules
Nginx location and rewrite rules are quite difficult to grasp at first.

Nginx will first match the requested url against "location =" declarations.
Such declaration are for exact literal matches. If one matches, it will
apply the content of the block and stops. This is a hard rule.

It will then look for "location ^~" declarations. Such declarations matches
when the requested url starts with the value of the location. No regexp
allowed. If one is found, it is applied and the parsing stops. This is
a hard rule.

Now Nginx will look for all others rules. "location ~" is a regexp search,
while "location ~*" is its case-insensitive counterpart. simple "location"
declarations will be checked after the regexps. Whenever one
matches the requested url, the block content is applied. Block contents can
contain additional "rewrite" rules. If such rules ends with `break`, then
the parsing stops. If it ends with `last`, the parsing starts again from
the top using the new url. If no flag is used, it continue to the next
matching rule.
 

