# A vanilla Docpad skeleton with Grunt build

This is an adaptation of [Luke Karrys' HTML5 Boilerplate with Grunt Docpad skeleton](https://github.com/lukekarrys/html5-boilerplate.docpad), with H5BP removed.

## Why the fork?
This fork keeps the Grunt child process and config file structure but it updates to the 0.4.0 *Gruntfile.js* file syntax, replaces the concat and min tasks with [grunt-contrib-uglify](https://github.com/gruntjs/grunt-contrib-uglify) and updates all other dependencies to the latest builds.

## What is different?

##### `grunt-config.json`
- This file is contains the object passed to `grunt.initConfig` in `grunt.js`. It has been put into its own file since it is used in `docpad.coffee` to build file lists for inclusion in the layout and deleting unused files.

##### `Gruntfile.js`
- This is the Grunt file. It runs `initConfig` with the `grunt-config.json` object. It also registers a `default` task with all the keys from the config file.

##### `docpad.coffee`
-  **These have been commented out until I have time to update these to work with the Uglify task syntax**. I added the helper functions [`getGruntedStyles`]() and [`getGruntedScripts`](). These functions will return all the compiled assets that contain `.min.(css|js)` with the correct base path.
- A [`writeAfter`]() DocPad event. It is based on [this gist](https://gist.github.com/3898915), with some additional functionality. It will run the `default` grunt command. Then it will use your `grunt-config.json` to delete the `src` files since they are no longer needed. It will also delete any empty directories in the 'out/' directory.

##### `layouts/default.html.eco`
- The script and style blocks have been replaced with calls to the helper functions described above.


## Getting Started

1. [Install DocPad](https://github.com/bevry/docpad)

1. Clone the project and run the server

	``` bash
	git clone git://github.com/ourmaninamsterdam/docpad-grunt-skeleton.git
	cd docpad-grunt-skeleton
	npm install
	docpad run
	```

1. [Open http://localhost:9778/](http://localhost:9778/)

1. Start hacking away by modifying the `src` directory


## License

This skeleton is made ["public domain"](http://en.wikipedia.org/wiki/Public_domain) using the [Creative Commons Zero](http://creativecommons.org/publicdomain/zero/1.0/), as such before you publish your website you should place your desired license here and within the `LICENSE.md` file.

If you are wanting to open-source your website, we suggest using the [Creative Commons Attribution License](http://creativecommons.org/licenses/by/3.0/) for content and the [MIT License](http://creativecommons.org/licenses/MIT/) for code. In which case you'd probably want to use the following as your license:

	Unless stated otherwise, all content is licensed under the [Creative Commons Attribution License](http://creativecommons.org/licenses/by/3.0/) and code licensed under the [MIT License](http://creativecommons.org/licenses/MIT/), © [Your Name](http://your.website)

If you are wanting to close-source your website, we'd suggest using the following:

	Copyright [Your Name](http://your.website). All rights reserved.

Other included things such as themes and libraries are likely already licensed by their own invidual licenses, so be sure to respect their licenses too.

Thanks, the DocPad team loves you.