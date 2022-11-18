# About

This repository contains content included on Microsoft Learn repos that appears as part of articles on [Microsoft Learn](https://learn.microsoft.com) properties. There are multiple repositories that contain Microsoft Learn content and writers often need to have the same content appear in multiple repos. The goal of this repo is to have one source for include files can be referenced in multiple repos in the `dependent_repositories` section of `.openpublishing.redirection.json`.

## Example use case and workflow

### Use case

The same set of instructions for creating a GitHub secret appears in 20+ articles on Microsoft Learn across four different repositories. There's a GitHub UI change and as a writer you want to update a screenshot and navigation path referenced in the articles quickly.

### Workflow

1. Add a new folder to the [reusable-content repo](https://github.com/MicrosoftDocs/reusable-content) for your service. The folder name should match the MSProd value for your content set. (_Note_: we may need to update existing content to meet this standard).
  
2. In the folder, add an include file with your content that follows the Learn guidelines for using includes. The include file can reference images in a `media` folder and should include metadata values.  For more information, see [Include reusable content in articles](https://review.learn.microsoft.com/en-us/help/platform/includes-best-practices).

3. Update `.openpublishing.publish.config.json` and add a section to `dependent_repositories` ([Learn platform user manual](https://review.learn.microsoft.com/en-us/help/platform/includes-best-practices?branch=main#cross-repo-includes)). To include images, you need to include the `build_entry_point` value in the `docsets_to_publish` section of `.openpublishing.publish.config.json` in the `path_to_root` value of the `dependent_repositories` property.

    ```json
       {
      "path_to_root": "docs/reusable-content",
      "url": "https://github.com/MicrosoftDocs/reusable-content",
      "branch": "main",
      "branch_mapping": {}
    }
    ```

4. Within your doc set, add the include to your article with `INCLUDE` syntax. Your path should include the build entry point.

    ```code
    [!INCLUDE [include](~/../docs/reusable-content/github-actions/authenticate-with-pat.md)]
    ```

5. Save and push your code. Verify that the include file appears within your article and that all images display. 

## Troubleshooting


## Contributing

This project welcomes contributions and suggestions.  Most contributions require you to agree to a
Contributor License Agreement (CLA) declaring that you have the right to, and actually do, grant us
the rights to use your contribution. For details, visit https://cla.opensource.microsoft.com.

When you submit a pull request, a CLA bot will automatically determine whether you need to provide
a CLA and decorate the PR appropriately (e.g., status check, comment). Simply follow the instructions
provided by the bot. You will only need to do this once across all repos using our CLA.

This project has adopted the [Microsoft Open Source Code of Conduct](https://opensource.microsoft.com/codeofconduct/).
For more information see the [Code of Conduct FAQ](https://opensource.microsoft.com/codeofconduct/faq/) or
contact [opencode@microsoft.com](mailto:opencode@microsoft.com) with any additional questions or comments.

## Legal Notices

Microsoft and any contributors grant you a license to the Microsoft documentation and other content
in this repository under the [Creative Commons Attribution 4.0 International Public License](https://creativecommons.org/licenses/by/4.0/legalcode),
see the [LICENSE](LICENSE) file, and grant you a license to any code in the repository under the [MIT License](https://opensource.org/licenses/MIT), see the
[LICENSE-CODE](LICENSE-CODE) file.

Microsoft, Windows, Microsoft Azure and/or other Microsoft products and services referenced in the documentation
may be either trademarks or registered trademarks of Microsoft in the United States and/or other countries.
The licenses for this project do not grant you rights to use any Microsoft names, logos, or trademarks.
Microsoft's general trademark guidelines can be found at http://go.microsoft.com/fwlink/?LinkID=254653.

Privacy information can be found at https://privacy.microsoft.com/en-us/

Microsoft and any contributors reserve all other rights, whether under their respective copyrights, patents,
or trademarks, whether by implication, estoppel or otherwise.
